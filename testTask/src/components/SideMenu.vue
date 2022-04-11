<template>
  <div class="menu">
    <SideMenuItem 
      v-for="item in menuItemsObj.menuItems" :key="item.id" :item="item"
      @SelectedItemRequest="SelectedItemRequest1" 
    >  
    </SideMenuItem>
  </div>
</template>

<script>

import axios from 'axios'
import SideMenuItem from './sideMenuItem.vue'

export default {
  name: 'SideMenu',
  components: {
    SideMenuItem,
  },
  data() {
    return {
      menuItemsObj: Object,
    }
  },
  methods: {
    SelectedItemRequest1(req, name) {
      this.$emit("SelectedItemProps", req, name)
    }
  },
  mounted() {
    axios
      .post('/', {requestedFuncIndex: 0})
      .then(response => {
        this.menuItemsObj = response.data
      })
  }  
}
</script>

<style scoped>
.menu {
  display: flex;
  flex-direction: column;
  gap: 5px;
  margin: 40px 0;
  text-transform: uppercase;  
}
</style>
