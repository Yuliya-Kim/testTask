<template>
  <div class="sections__item">
    <h2>{{section.name}}</h2>
    <div class="options-list">
      <SettingsSectionOptions
        v-for="options in section.options" :key="options.id" :options="options"> 
      </SettingsSectionOptions>
    </div>
  </div>
</template>

<script>

import SettingsSectionOptions from './contentSettingsSectionOptions.vue'

export default {
  name: 'SettingsSection',
  components: {
    SettingsSectionOptions,
  },
  props: {
    section: Array,
  },
}
</script>

<style scoped>
.sections__item {
  padding: 10px;
  background: white;
  border-radius: 10px;
  border: 1px solid lightgrey;
}

.options-list {
    display: flex;
    flex-direction: column;
}


</style>
