<template>
  <div class="container">
    <h1>Vue-Quill-Editor demo</h1>
    <QuillEditorDemo></QuillEditorDemo>
    <br />
    <h1>WangEditor3 demo</h1>
    <WangEditorDemo :catchData="catchData"></WangEditorDemo>
    <br />
    <h1>Tinymce demo</h1>
    <Tinymce></Tinymce>
  </div>
</template>

<script>
// @ is an alias to /src
import QuillEditorDemo from "@/components/Vue-Quill-Editor/quillEditor";
import WangEditorDemo from "@/components/wangEditor/index";
import Tinymce from "@/components/tinymce/demo";

export default {
  name: "EditorDemo",
  components: {
    QuillEditorDemo,
    WangEditorDemo,
    Tinymce
  },
  data() {
    return {
      content: ""
    };
  },
  methods: {
    catchData(value) {
      this.content = value; //在这里接受子组件传过来的参数，赋值给data里的参数
    }
  }
};
</script>
