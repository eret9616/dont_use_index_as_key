<template>
  <div id="app">
    <button @click="handleClick">点击切换例子</button>
    {{getCount()}}
    <template v-if="switched">
      <p>正常的例子：删除哪行，的确是删了哪行</p>
      <div v-for="(item, index) in data" :key="index">
        <StateComponent :name="`依赖于状态的属性+${item.name}`"/>
        <button @click="handleDelete(index)">删除这一行</button>
      </div>
    </template>
    <template v-else>
      <p>异常的例子：删除哪行，不符合预期</p>
      <div v-for="(item, index) in data" :key="index">
        <StaticComponent :name="`不依赖于状态的属性`"/>
        <button @click="handleDelete(index)">删除这一行</button>
      </div>
    </template>
  </div>
</template>

<script>
import StateComponent from "./components/StateComponent";
import StaticComponent from "./components/StaticComponent";

export default {
  name: "App",
  components: {
    StateComponent,
    StaticComponent
  },
  data() {
    return {
      switched: false,
      data: [
        { name: "ftd1" },
        { name: "ftd2" },
        { name: "ftd3" },
        { name: "ftd4" },
        { name: "ftd5" },
        { name: "ftd6" },
        { name: "ftd7" },
        { name: "ftd8" }
      ]
    };
  },
  methods: {
    handleClick() {
      this.switched = !this.switched;
    },
    handleDelete(index) {
      this.data.splice(index, 1);
    },
    getCount() {
      console.log("第1阶段渲染：主体render");
    }
  }
};
</script>

<style>
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
