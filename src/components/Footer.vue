<template>
  <footer class="footer">
    <span class="footer-logo"> </span>
    <span class="footer-text">
      <span>
        1.本功能之監測數據所有權屬雲林縣環境保護局所有，未經同意請勿任意引用。<br />
        2.微型感測器測值僅供室內濃度變化參考，多數場所會受周邊環境大氣所影響。<br />
        3.因感測器元件易受溫溼度等干擾，請民眾仍以參照標準檢測方法採樣數據為主。<br />
      </span>
    </span>
    <span class="footer-view">
      <div class="footer-view-img" />
      <div class="footer-view-text">
        <div>瀏覽人次</div>
        <div>12,345,678</div>
      </div>
    </span>
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
    });
    return {
      viewCount,
    };
  },
};
</script>

<style scoped>
.footer {
  width: 100%;
  height: 15vh;
  padding: 0 15px;
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
  margin-left: -10vh;
}
.footer-view {
  width: 10%;
  color: green;
  display: flex;
  font-weight: bolder;
  height: 50%;
  gap: 10px;
}
.footer-view-img {
  width: 100%;
  background-image: url("../assets/viewer.png");
  background-position: center;
  background-size: cover;
}
.footer-view-text {
  text-align: center;
}
</style>