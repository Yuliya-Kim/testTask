<template>
  <div>
    <div class="beep">{{Beep.message}}</div>
  </div>
</template>

<script>
import axios from 'axios'

export default {
  name: 'ContentBeep',
  data() {
    return {
      Beep: Object,
    }
  },
  mounted() {
    axios
      .post('/', {requestedFuncIndex: 5})
      .then(response => {
        this.Beep = response.data
      })
  }
}
</script>

<style scoped>
.beep {
  animation: beep .3s linear 2; 
}

@keyframes beep {
  100% { 
    opacity: 0;
  } 
}
</style>
