<template>
  <div class="">
    <div>{{Help.content}}</div>
  </div>
</template>

<script>
import axios from 'axios'

export default {
  name: 'ContentHelp',
  data() {
    return {
      Help: Object,
    }
  },
  mounted() {
    axios
      .post('/', {requestedFuncIndex: 4})
      .then(response => {
        this.Help = response.data
      })
  }
}
</script>

<style scoped>

</style>
