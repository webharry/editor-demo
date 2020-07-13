<template>
  <el-form ref="form" :form="form" @submit="handleSubmit">
    <el-tag color="#108ee9">文章编辑</el-tag>
    <el-form-item
      :label-col="labelCol"
      :wrapper-col="wrapperCol"
      label="文章分类"
    >
      <el-select style="width: 100%" v-model="form.region">
        <el-option value="0">请选择分类</el-option>
        <el-option
          v-for="(cate, index) in cate_list"
          :key="index"
          :value="cate.category_id"
          >{{ cate.category_name }}</el-option
        >
      </el-select>
    </el-form-item>
    <el-form-item
      :label-col="labelCol"
      :wrapper-col="wrapperCol"
      label="文章名称"
    >
      <el-input></el-input>
    </el-form-item>
    <el-form-item
      :label-col="labelCol"
      :wrapper-col="wrapperCol"
      label="关键词"
      help="关键词用英文逗号','分隔"
    >
      <el-input></el-input>
    </el-form-item>
    <el-form-item
      :label-col="labelCol"
      :wrapper-col="wrapperCol"
      label="文章摘要"
    >
      <el-input type="textarea" v-model="form.desc"></el-input>
    </el-form-item>
    <el-form-item
      :label-col="labelCol"
      :wrapper-col="wrapperCol"
      label="文章插图"
    >
      <el-upload
        name="article_pic"
        listType="picture-card"
        class="avatar-uploader"
        :showUploadList="false"
        action="https://www.mocky.io/v2/5cc8019d300000980a055e76"
        :beforeUpload="beforeUpload"
        @change="handleChange"
      >
        <img v-if="imageUrl" :src="imageUrl" alt="avatar" />
        <div v-else>
          <el-icon :type="loading ? 'loading' : 'plus'" />
          <div class="ant-upload-text">选择头像</div>
        </div>
      </el-upload>
    </el-form-item>
    <el-form-item
      :label-col="labelCol"
      :wrapper-col="wrapperCol"
      label="文章内容"
    >
      <!--使用 Tinymce.vue 组件-->
      <tinymceEditor
        v-model="msg"
        :disabled="disabled"
        @onClick="onClick"
        ref="editor"
      >
      </tinymceEditor>
    </el-form-item>
    <el-form-item :label-col="labelCol" :wrapper-col="wrapperCol">
      <div>
        <el-button
          type="primary"
          html-type="submit"
          class="login-form-button"
          style="margin-right: 5%;"
        >
          保存
        </el-button>

        <el-button type="danger" class="login-form-button" @click="resetFields">
          重置
        </el-button>
      </div>
    </el-form-item>
  </el-form>
</template>
<script>
// import { EditArticle, SaveArticle } from "../../axios/api";
import TinyMce from "@/components/tinymce/index";
function getBase64(img, callback) {
  const reader = new FileReader();
  reader.addEventListener("load", () => callback(reader.result));
  reader.readAsDataURL(img);
}

export default {
  name: "MenuEdit",
  components: {
    tinymceEditor: TinyMce,
  },
  data: function() {
    return {
      loading: false,
      form: {
        msg: "",
      },
      article_id: this.$route.query.article_id,
      article: [],
      cate_list: [],
      imageUrl: "",
      head_pic: "",
      labelCol: {
        xs: { span: 24 },
        sm: { span: 5 },
      },
      wrapperCol: {
        xs: { span: 24 },
        sm: { span: 12 },
      },
      disabled: false,
      msg: "欢迎来到全新编辑器",
    };
  },
  created() {
    // EditArticle({
    //   article_id: this.article_id,
    // })
    //   .then((response) => {
    //     if (response.data.code == 1) {
    //       this.article = response.data.data.article;
    //       this.cate_list = response.data.data.cate_list;
    //       this.imageUrl = response.data.data.article.article_pic;
    //     } else {
    //       this.msg = response.data.msg;
    //       this.openNotification();
    //     }
    //   })
    //   .catch((err) => {
    //     console.log(err);
    //   });
  },
  methods: {
    openNotification() {
      this.$notification.open({
        message: "提醒框",
        description: this.msg,
      });
    },

    handleSubmit(e) {
      e.preventDefault();
      this.form.validateFields((errors, values) => {
        if (errors) {
          console.log(errors);
        } else {
          values.article_id = this.article_id;
          values.article_pic = this.article_pic;
          this.postSubmit(values);
        }
      });
    },
    resetFields() {
      this.form.resetFields();
    },
    postSubmit(param) {
      //   SaveArticle(param)
      //     .then((res) => {
      //       if (res.data.code == 1) {
      //         this.$message.success(res.data.msg, 2);
      //       } else {
      //         this.$message.error(res.data.msg, 2);
      //       }
      //     })
      //     .catch((error) => {
      //       console.log(error);
      //     });
    },
    handleChange(info) {
      if (info.file.status === "uploading") {
        this.loading = true;
        return;
      }
      if (info.file.status === "done") {
        this.article_pic = info.file.response.thumbUrl;
        // Get this url from response in real world.
        getBase64(info.file.originFileObj, (imageUrl) => {
          this.imageUrl = imageUrl;
          this.loading = false;
        });
      } else if (info.file.status === "error") {
        this.$message.error("上传失败", 2);
      }
    },
    beforeUpload(file) {
      const isJPG = file.type === "image/jpeg";
      if (!isJPG) {
        this.$message.error("You can only upload JPG file!");
      }
      const isLt2M = file.size / 1024 / 1024 < 2;
      if (!isLt2M) {
        this.$message.error("Image must smaller than 2MB!");
      }
      return isJPG && isLt2M;
    },
    //鼠标单击的事件
    onClick(e, editor) {
      console.log("Element clicked");
      console.log(e);
      console.log(editor);
    },
  },
};
</script>

<style scoped></style>
