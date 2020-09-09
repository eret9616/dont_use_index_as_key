<template>
  <span>
    {{getCount()}}
    {{name}}
    {{Math.floor(Math.random() * 1000)}}
    【打开控制台查看日志，发现的确会重新render】
  </span>
</template>
<script>
export default {
  props: {
    name: String
  },
  methods: {
    getCount() {
      console.count(
        "第2阶段渲染：依赖props的组件render，因为name依赖了响应式数据"
      );
    }
  }
};
</script>