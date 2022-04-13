<template>
  <div class="wrapper">
    <div class="title">
      <div>雲林縣室內空氣品質</div>
      <div>連續監測即時資訊</div>
    </div>
    <main class="content">
      <Box v-for="item in 8" :key="item" />
    </main>
    <Footer />
  </div>
</template>

<script>
import axios from "axios";
import { onMounted, reactive } from "vue";
import Box from "./components/Box.vue";
import Footer from "./components/Footer.vue";
export default {
  name: "App",
  components: {
    Box,
    Footer,
  },
  setup() {
    let arr = reactive({ data: [] });
    onMounted(() => {
      const url = "http://localhost:3000/api_v2/test/avid";
      const list = ["A123", "B122", "C124", "D789"];
      let promiseList = list.map((el) => axios.put(`${url}?id=${el}`));
      Promise.all(promiseList).then((res) => {
        arr.data = res.map((el) => el["data"]);
      });
    });
    return {
      arr,
    };
  },
};
</script>

<style>
* {
  font-family: "微軟正黑體";
  box-sizing: border-box;
}
body,
html {
  height: 98%;
  padding: 0px;
  margin: 0px;
}
body {
  max-height: 98%;
  width: 100%;
  background-image: url("assets/background.jpg");
  background-repeat: no-repeat;
  background-position: center;
  background-size: cover;
}
.wrapper {
  width: 100%;
}
.title {
  text-align: center;
  font-size: 48px;
  font-weight: bolder;
  padding-bottom: 15px;
}
.content {
  width: 90%;
  margin: 0 auto;
  display: flex;
  flex-wrap: wrap;
  justify-content: center;
  padding-bottom: 30px;
  column-gap: 50px;
  row-gap: 20px;
}
</style>
