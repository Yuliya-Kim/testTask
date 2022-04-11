<template>
  <div class="devices-wrap">
    <DeviceCard 
      v-for="device in devicesInfo.devices" :key="device.id" :device="device">
    </DeviceCard>
  </div>
</template>

<script>
import axios from 'axios'

import DeviceCard from './deviceCard.vue'

export default {
  name: 'ContentInformation',
  components: {
    DeviceCard,
  },
  data() {
    return {
      devicesInfo: Object,
    }
  },
  mounted() {
    axios
      .post('/', {requestedFuncIndex: 1})
      .then(response => {
        this.devicesInfo = response.data
      })
  }
}
</script>

<style scoped>
.devices-wrap {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(350px, 1fr));
  grid-gap: 30px;
}
</style>
