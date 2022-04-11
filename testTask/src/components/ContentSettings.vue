<template>
  <div class="sections">
    <SettingsSection v-for="setting in Settings.sections" :key="setting.id" :section="setting"/>
  </div>
</template>

<script>
import axios from 'axios'
import SettingsSection from './contentSettingsSection.vue'

export default {
  name: 'ContentSettings',
  components: {
    SettingsSection,
  },
  data() {
    return {
      Settings: Object,
    }
  },
  mounted() {
    axios
      .post('/', {requestedFuncIndex: 2})
      .then(response => {
        this.Settings = response.data
      })
  }
}
</script>

<style scoped>
.sections {
  display: flex;
  flex-direction: column;
  gap: 30px;
}
</style>
