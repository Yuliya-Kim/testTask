<template>
  <div class="content-main">
    <h1 class="content-main__title">{{contentName}}</h1>
    <hr>
    <div v-if="contentReqNum === 1" ><ContentInformation/></div>
    <div v-else-if="contentReqNum === 2"><ContentSettings/></div>
    <div v-else-if="contentReqNum === 3"><ContentControls/></div>
    <div v-else-if="contentReqNum === 4"><ContentHelp/></div>
    <div v-else-if="contentReqNum === 5"><ContentBeep/></div>
  </div>
</template>

<script>
import ContentInformation from './ContentInformation.vue'
import ContentSettings from './ContentSettings.vue'
import ContentControls from './ContentControls.vue'
import ContentHelp from './ContentHelp.vue'
import ContentBeep from './ContentBeep.vue'

export default {
  name: 'ContentMain',
  components: {
    ContentInformation,
    ContentSettings,
    ContentControls,
    ContentHelp,
    ContentBeep,
  },
  props: {
    contentReqNum: Number,
    contentName: String,
  },
}
</script>

<style scoped>
.content-main {
  flex-basis: calc(100% - 200px);
  margin: 20px 40px;
}
.content-main__title {
  text-transform: uppercase;
}
</style>
