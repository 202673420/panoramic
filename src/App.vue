<template>
  <div id="app">
    <!-- <img src="./assets/logo.png"> -->
    <router-view/>
  </div>
</template>

<script>
import { useFiveState } from '@realsee/five/vue'
import { work } from "@realsee/open-works/virtual/81RojBlJQdVTglNNMr/work.json"
export default {
  name: 'App',
  data(){
    return {
      // five:null
    }
  },
  mounted() {
  const five = new useFiveState ({
    backgroundAlpha: 0.5,
    imageOptions: {
      size: 1024,
      quality: 70
    },
    onlyRenderIfNeeds: true
  });
  // 将渲染视图的 canvas 添加到 DOM 中
  five.appendTo(document.getElementById('app'));
  // 如果显示区域需要变动，在变动时请调用 refresh 重置显示参数
  window.addEventListener('resize', () => five.refresh());
  // 获取当前 VR 的房间数据，加载进来
  five.load(work);
},
}

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
