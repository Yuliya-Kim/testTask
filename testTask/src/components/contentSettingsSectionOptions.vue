<template>
  <div class="options-list__item">
    <div class="option">
      <span class="option__name">{{options.name}}</span>
      <label :class = "(options.type === '__switch')?'switch':'checkbox'">
        <input type="checkbox" :checked="(options.state === true) ? true : false">
        <span :class = "(options.type === '__switch')?'slider round':'checkmark'"></span>
      </label>
    </div>
  </div>  
</template>

<script>
export default {
  name: 'SettingsSectionOptions',
  props: {
    options: Object,
  },
}
</script>

<style scoped>
.options-list__item {
  margin: 10px 0;
}
.option {
  display: flex;
  align-items: center;
  gap: 15px;
}
.option__name {
  min-width: 90px;
}
</style>
