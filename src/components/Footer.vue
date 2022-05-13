<template>
  <footer class="footer">
    <span class="footer-logo"></span>
    <span class="footer-text">
      <span>
        1.本功能之監測數據所有權屬雲林縣環境保護局所有，未經同意請勿任意引用。<br />
        2.微型感測器測值僅供室內濃度變化參考，多數場所會受周邊環境大氣所影響。<br />
        3.因感測器元件易受溫溼度等干擾，請民眾仍以參照標準檢測方法採樣數據為主。<br />
      </span>
    </span>
    <div class="footer-browse">
      <div class="footer-image">
        <img src="../assets/viewer.png" width="50" />
      </div>
      <div class="footer-main">
        <p>瀏覽人次</p>
        <p id="area"></p>
      </div>
    </div>
  </footer>
</template>

<script>
import { onMounted, ref } from "vue";
export default {
  name: "Footer",
  setup() {
    let viewCount = ref(0);
    onMounted(() => {
      viewCount.value++;
      let browse = document.createElement("script");
      let browseArea = document.getElementById("area");
      browse.setAttribute("language", "javascript");
      browse.setAttribute("type", "text/javascript");
      browse.setAttribute(
        "src",
        "//counter1.fc2.com/counter.php?id=38204634&main=1"
      );
      browseArea.appendChild(browse);
    });
    return {
      viewCount,
    };
  },
};
</script>

<style scoped>
* {
  margin: 0;
  padding: 0;
}
.footer {
  box-sizing: border-box;
  width: 100%;
  height: 16.5vh;
  padding-top: 1.5vh;
  padding-right: 2vh;
  padding-left: 2vh;
  display: flex;
  justify-content: space-between;
}
.footer-logo {
  width: 20%;
  background-image: url("../assets/logo.gif");
  background-position: center;
  background-size: cover;
  height: 50%;
}
.footer-text {
  color: white;
  font-weight: bolder;
  font-size: 2vh;
  height: 100%;
  display: flex;
  align-items: flex-end;
  margin-left: -15vh;
}
.footer-browse {
  display: inline-flex;
  font-weight: bold;
  vertical-align: top;
}
.footer-main {
  flex: 1;
  text-align: center;
  font-size:2.5vh;
  color: green;
  white-space: nowrap;
}
.footer-image {
  flex: 1;
  height: 100%;
}
</style>