<template>
  <div class="card" :style="{ width: width }">
    <div class="card-title">雲林縣環境保護局</div>
    <div class="card-body">
      <div style="padding-bottom: 15px">
        <span>CO<sub>2</sub></span>
        <span>值</span>
        <span>PPM</span>
      </div>
      <div>
        <span>PM<sub>2.5</sub></span>
        <span>值</span>
        <span>μg/m<sup>3</sup></span>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "Box",
  props: ["width"],
};
</script>

<style scoped>
.card {
  background: rgb(226, 240, 217);
  border-radius: 15px;
}
.card-title {
  background: rgb(169, 209, 142);
  padding: 0 15px;
  color: white;
  font-weight: bolder;
  border-radius: 15px;
}
.card-body {
  padding: 15px;
  font-weight: bolder;
}
.card-body div {
  display: flex;
  justify-content: space-between;
}
</style>