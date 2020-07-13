# 一、富文本编辑器调研
背景：近期有需求要做富文本编辑器，故网上找了几个比较有名的demo了例子，做些总结，方便后续实践。

# 二、常见的富文本编辑器比较：
##  1、tinymce 富文本编辑器
源码地址：https://github.com/tinymce/tinymce-vue  star 913

优点：
* tinymce是一款易用、且功能强大的所见即所得的富文本编辑器。同类程序有：UEditor、Kindeditor、Simditor、CKEditor、wangEditor、Suneditor、froala等等。
* 老牌做富文本的公司打造，文档完善，配置自由度高。
* PC端和移动端兼容

缺点：
* 个人觉得引入方式不快捷

文档：https://www.tiny.cloud/docs/quick-start/
中文文档：http://tinymce.ax-z.cn/
语言下载地址：https://www.tiny.cloud/get-tiny/language-packages/

项目实践：
Vue-Cli 3+tinymce 5 富文本编辑器整合：https://learnku.com/articles/34553
在 Vue 项目中引入 tinymce 富文本编辑器:https://www.cnblogs.com/wisewrong/p/8985471.html
https://liubing.me/vue-tinymce-5.html
tinymce-vue 使用总结：https://www.jianshu.com/p/675eae30b7df


## 2、smeditor 
源码地址：https://github.com/GeekPark/smeditor  star 295
基于 Vue.js 2.0+ 石墨文档样式的富文本编辑器组件

优点：
* 轻, 快 48 KB，代码精简, 适合二次开发


## 3、vditor   
源码地址：https://github.com/Vanessa219/vditor  star 775
官方介绍：Vditor 是一款浏览器端的 Markdown 编辑器，支持所见即所得、即时渲染（类似 Typora）和分屏预览模式。它使用 TypeScript 实现，支持原生 JavaScript、Vue、React、Angular，提供桌面版。


## 4、vue-quill-editor  
源码地址：https://github.com/surmon-china/vue-quill-editor  star 5.7k

优点：
* 兼容PC和移动端，对vue最好用的一个轻量级编辑器
* 图片上传方式是base64,默认转换且不上传到服务器

缺点：
* 文档是英文，熟悉英文的老铁忽略

项目实践：
https://juejin.im/post/5ceb5e47f265da1bb679f619
https://juejin.im/post/5ceb5e47f265da1bb679f619
vue+elementUI中实践：https://www.jianshu.com/p/4e00f11583fa
https://panjiachen.github.io/vue-element-admin-site/zh/feature/component/rich-editor.html#tinymce

## 5、wangeditor 
源码地址：https://www.kancloud.cn/wangfupeng/wangeditor3/335769

优点：
* 轻量、简洁、易用、开源免费
* 图片上传有两种方式：1、base64且不上传。2、通过URL方式上传
* 国人写的，中文文档：https://www.kancloud.cn/wangfupeng/wangeditor3/335769

缺点：
* 移动端样式存在兼容性问题
* 上传图片到服务器

项目实践：https://www.jianshu.com/p/e72e1e0612cd


移动端
## 6、ueditor  
源码地址：https://github.com/fex-team/ueditor   star 5.2k、

优点：
* 百度前端的开源项目，功能强大，基于 jQuery，但已经没有再维护，而且限定了后端代码，修改起来比较费劲

缺点：
* ui 真的不好看，官方很久没更新了


## 7、neditor 
源码地址：https://github.com/notadd/neditor  star 1.8k

优点：
* 基于ueditor的升级，界面更现代化，支持HTTPS


## 8、artEditor 
源码地址：https://github.com/baixuexiyang/artEditor  star 251
据官方介绍，artEditor是一款基于jQuery的移动端富文本编辑器，支持插入图片，后续完善其他功能。新增图片上传之前压缩功能 demo，为了更好的效果请将浏览器设置为手机模式。


# editor-demo

## Project setup
```
npm install
```

### Compiles and hot-reloads for development
```
npm run serve
```

### Compiles and minifies for production
```
npm run build
```

### Run your tests
```
npm run test
```

### Lints and fixes files
```
npm run lint
```

### Customize configuration
See [Configuration Reference](https://cli.vuejs.org/config/).
