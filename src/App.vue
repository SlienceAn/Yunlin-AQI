<template>
  <div class="wrapper">
    <div class="title">
      <div>雲林縣室內空氣品質</div>
      <div>連續監測即時資訊</div>
    </div>
    <div class="content">
      <Box
        v-for="item in [0, 1, 2, 3, 4, 5, 6, 7]"
        :key="item"
        width="22%"
        :DeviceIdx="item"
      />
    </div>
    <div class="second-content">
      <Box
        v-for="item in [8, 9, 10, 11, 12]"
        :key="item"
        width="18%"
        :DeviceIdx="item"
      />
    </div>
    <Footer />
  </div>
</template>

<script>
import Box from "./components/Box.vue";
import Footer from "./components/Footer.vue";
export default {
  name: "App",
  components: {
    Box,
    Footer,
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
  background-position: 100% 21%;
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
.second-content {
  display: flex;
  flex-wrap: wrap;
  justify-content: center;
  column-gap: 30px;
}
</style>
