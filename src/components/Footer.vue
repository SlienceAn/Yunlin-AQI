<template>
  <footer class="footer">
    <span class="footer-logo"> </span>
    <span class="footer-text">
      <div>
        1.本功能之監測數據所有權屬雲林縣環境保護局所有，未經同意請勿任意引用。
      </div>
      <div>
        2.微型感測器測值僅供室內濃度變化參考，多數場所會受周邊環境大氣所影響。
      </div>
      <div>
        3.因感測器元件易受溫溼度等干擾，請民眾仍以參照標準檢測方法採樣數據為主
      </div>
    </span>
    <span class="footer-view">
        <span></span>
        <span>
            <div>瀏覽人次</div>
            <div>123,456,789</div>
        </span>
    </span>
  </footer>
</template>

<script>
export default {
  name: "Footer",
};
</script>

<style scoped>
.footer {
  padding: 0 10px;
  display: flex;
  justify-content: space-between;
}
.footer-logo {
  width: 20%;
  background-image: url("../assets/logo.gif");
  background-position: center;
  background-size: cover;
}
.footer-text {
  color: white;
  font-weight: bolder;
}
.footer-view {
}
</style>