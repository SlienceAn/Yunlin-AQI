<template>
  <div class="wrapper">
    <div class="title">
      <div>雲林縣室內空氣品質</div>
      <div>連續監測即時資訊</div>
    </div>
    <div class="content">
      <Box
        v-for="item in [0, 1, 2, 3]"
        :key="item"
        width="25%"
        :DeviceIdx="item"
      />
    </div>
    <div class="second-content">
      <Box
        v-for="item in [4, 5, 6, 7]"
        :key="item"
        width="25%"
        :DeviceIdx="item"
      />
    </div>
    <div class="third-content">
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
  height: 100%;
  padding: 0px;
  margin: 0px;
}
body {
  max-height: 108%;
  width: 100%;
  background-image: url("assets/background2.jpg");
  background-repeat: no-repeat;
  background-position: bottom right;
  background-size: cover;
}
.wrapper {
  width: 100%;
}
.title {
  text-align: center;
  font-size: 6vh;
  font-weight: bolder;
  min-height: 15vh;
}
.content,
.second-content {
  min-height: 20vh;
  display: flex;
  justify-content: space-between;
  width: 90%;
  margin: 0 auto;
  padding: 2vh 0;
  gap: 5vh;
}
.third-content {
  min-height: 20vh;
  display: flex;
  justify-content: space-between;
  width: 95%;
  margin: 0 auto;
  padding: 2.5vh 0;
}
</style>
