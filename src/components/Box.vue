<template>
  <div class="card" :style="{ width: width }">
    <div v-if="!isShow" class="card-title">--</div>
    <div v-else class="card-title">
      {{ deviceName.data.DeviceName }}
    </div>
    <div class="card-body">
      <div v-for="val in data.data.Device" :key="val.TagName">
        <div
          class="card-body-content"
          v-if="val.TagName === 'CO2' || val.TagName === 'PM2.5'"
        >
          <span v-if="val.TagName === 'CO2'"> CO<sub>2</sub></span>
          <span v-else>PM<sub>2.5</sub></span>
          <span v-if="isShow && val.Value > 0">{{ val.Value }}</span>
          <span v-else>----</span>
          <span>{{ val.Unit }}</span>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import axios from "axios";
import { onMounted, reactive, ref } from "vue";
export default {
  name: "Box",
  props: ["width", "DeviceIdx"],
  setup(props) {
    const data = reactive({ data: {} });
    const deviceName = reactive({ data: {} });
    const isShow = ref(false);
    onMounted(() => {
      fetchData();
      setInterval(() => {
        fetchData();
      }, 3 * 60 * 1000);
    });
    const fetchData = () => {
      const url = `http://www.jnc-demo.tw:11223/JSONDeviceCH?DeviceIdx=${props.DeviceIdx}&Key=VHNwb3J0AQ%3D%3D`;
      const nameUrl = `http://www.jnc-demo.tw:11223/JSONDevice?Idx=${props.DeviceIdx}&Key=VHNwb3J0AQ%3D%3D`;
      const dataPromise = axios.get(url);
      const namePromise = axios.get(nameUrl);
      Promise.all([dataPromise, namePromise])
        .then((res) => {
          data.data = res[0].data;
          deviceName.data = res[1].data;
          console.log(deviceName.data);
          isShow.value = true;
        })
        .catch((err) => console.log(err));
    };
    return {
      data,
      deviceName,
      props,
      isShow,
    };
  },
};
</script>

<style scoped>
.card {
  background: rgb(226, 240, 217);
  border-radius: 2.5vh;
}
.card-title {
  background: rgb(169, 209, 142);
  padding: 1vh 1.5vh;
  color: white;
  font-weight: bolder;
  font-size: 2.3vh;
  border-radius: 2.5vh;
}
.card-body {
  font-weight: bolder;
  display: flex;
  flex-direction: column;
  font-size: 2.3vh;
  padding-left: 2vh;
  padding-right: 2vh;
  padding-top: 2vh;
}
.card-body-content {
  display: flex;
  justify-content: space-between;
  padding-bottom: 2vh;
}
</style>