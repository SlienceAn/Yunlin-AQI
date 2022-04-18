<template>
  <div class="card" :style="{ width: width }">
    <div class="card-title">{{ deviceName.data.DeviceName }}</div>
    <div class="card-body">
      <div v-for="val in data.data.Device" :key="val.TagName">
        <div
          class="card-body-content"
          v-if="val.TagName === 'CO2' || val.TagName === 'PM2.5'"
        >
          <span v-if="val.TagName === 'CO2'"> CO<sub>2</sub> </span>
          <span v-else>PM<sub>2.5</sub></span>
          <span v-if="val.Value">{{ val.Value }}</span>
          <span v-else>--</span>
          <span>{{ val.Unit }}</span>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import axios from "axios";
import { onMounted, reactive } from "vue";
export default {
  name: "Box",
  props: ["width", "DeviceIdx"],
  setup(props) {
    const data = reactive({ data: {} });
    const deviceName = reactive({ data: {} });
    onMounted(() => {
      const url = `http://www.jnc-demo.tw:11223/JSONDeviceCH?DeviceIdx=${props.DeviceIdx}&Key=VHNwb3J0AQ%3D%3D`;
      const nameUrl = `http://www.jnc-demo.tw:11223/JSONDevice?Idx=${props.DeviceIdx}&Key=VHNwb3J0AQ%3D%3D`;
      const dataPromise = axios.get(url);
      const namePromise = axios.get(nameUrl);
      Promise.all([dataPromise, namePromise])
        .then((res) => {
          data.data = res[0].data;
          deviceName.data = res[1].data;
        })
        .catch((err) => console.log(err));
    });
    return {
      data,
      deviceName,
      props,
    };
  },
};
</script>

<style scoped>
.card {
  background: rgb(226, 240, 217);
  border-radius: 15px;
}
.card-title {
  background: rgb(169, 209, 142);
  padding: 5px 15px;
  color: white;
  font-weight: bolder;
  border-radius: 15px;
}
.card-body {
  font-weight: bolder;
  display: flex;
  flex-direction: column;
  padding-left: 15px;
  padding-right: 15px;
  padding-top: 15px;
}
.card-body-content {
  display: flex;
  justify-content: space-between;
  padding-bottom: 15px;
}
</style>