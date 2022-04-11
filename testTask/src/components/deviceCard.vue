<template>
  <div class="device-card">
    <h2>Устройство {{device.id + 1}}</h2>

    <span v-if="device.status == true" class="active-text">Активно</span>
    <span v-else class="not-active-text">Не активно</span>
    <div :class = "(device.status == true)?'dot active':'dot not-active'"></div>

    <div class="device-card__prop">
      <span>Наименование: </span><span class="text-bold"> {{device.name}}</span>
    </div>
    <div class="device-card__prop">
      <span>Серийный номер: </span><span class="text-bold">{{device.serialNumber}}</span>
    </div>
    <div class="device-card__prop">
      <span>Описание: </span><span>{{device.description}}</span>
    </div>

  </div>
</template>

<script>

export default {
  name: 'DeviceCard',
  props: {
    device: Object
  },
}
</script>

<style scoped>

.device-card {
  position: relative;
  margin: 1px;
  padding: 10px;
  background: white;
  border-radius: 10px;
  -webkit-box-shadow: 4px 4px 8px 0px rgb(34 60 80 / 20%);
  -moz-box-shadow: 4px 4px 8px 0px rgb(34 60 80 / 20%);
  box-shadow: 4px 4px 8px 0px rgb(34 60 80 / 20%);
}
.device-card:hover {
  margin: -1px 0 1px 0;
  border: 1px solid #e9e9e9;
  -webkit-box-shadow: 8px 8px 9px 0px rgba(34, 60, 80, 0.2);
  -moz-box-shadow: 8px 8px 9px 0px rgba(34, 60, 80, 0.2);
  box-shadow: 8px 8px 9px 0px rgba(34, 60, 80, 0.2);
}

.active-text {
  color: rgb(0, 186, 0);
}
.not-active-text {
  color: #787878;
}

.dot {
  position: absolute;
  top: 10px;
  right: 10px;
  width: 15px;
  height: 15px;
  border-radius: 50%;
}
.active {
  background: lawngreen;
}
.not-active {
  background: #cecece;
}

.device-card__prop {
  margin: 8px 0;
}

</style>
