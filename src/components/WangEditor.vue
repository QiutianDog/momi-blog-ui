<template>
  <v-app>
    <div id="demo"></div>
  </v-app>
</template>

<script>
// 引入 wangEditor
import wangEditor from 'wangeditor'
// 引入 highlight
import hljs from 'highlight.js'

export default {
  name: "WangEditor",
  data: () => ({
      editor: null,
      editorData: '',
  }),
  mounted() {
    const editor = new wangEditor(`#demo`)
    // 配置 onchange 回调函数，将数据同步到 vue 中
    editor.config.onchange = (newHtml) => {
      this.editorData = newHtml
    }
    // 创建编辑器
    editor.highlight = hljs
    editor.create()
    this.editor = editor
  },
  beforeDestroy() {
    // 调用销毁 API 对当前编辑器实例进行销毁
    this.editor.destroy()
    this.editor = null
  }
}
</script>

<style scoped>

</style>