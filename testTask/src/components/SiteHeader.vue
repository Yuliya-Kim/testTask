<template>
  <div class="header">
    <h1 class="header__title">{{headerTitle}}</h1>
  </div>
</template>

<script>
export default {
  name: 'SiteHeader',
  props: {
    headerTitle: String
  }
}
</script>

<style scoped>
.header {
  display: flex;
  align-items: center;
  height: 60px;
  color: white;
  background: #8c8c8c;
  border-bottom: 2px solid yellow;
}
.header__title {
  margin: 0 0 0 10px;
}
</style>
