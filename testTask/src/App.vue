<template>
  <SiteHeader headerTitle="Тестовое задание"/>
  <div class="content">
    <div class="aside">
      <SideMenu @SelectedItemProps="SelectedItemProps1"/>
    </div>
    <ContentMain :contentReqNum="contentReqNum" :contentName="contentName"/>
  </div> 
</template>

<script>

import SiteHeader from './components/SiteHeader.vue'
import SideMenu from './components/SideMenu.vue'
import ContentMain from './components/ContentMain.vue'

export default {
  name: 'App',
  components: {
    SiteHeader,
    SideMenu,
    ContentMain,
  },
  data()  {
    return {
      contentReqNum: null,
      contentName: null
    }
  },
  methods: {
    SelectedItemProps1(req, name) {
      this.contentReqNum = req
      this.contentName = name 
    }
  }
}
</script>

<style>
.content {
  display: flex;
  background: #f4f8f9;
}
.aside {
  flex: 0 1 200px;
  height: 100vh;
  background: white;
  -webkit-box-shadow: 4px 0px 9px 0px rgb(34 60 80 / 20%);
  -moz-box-shadow: 4px 0px 9px 0px rgba(34, 60, 80, 0.2);
  box-shadow: 4px 0px 9px 0px rgb(34 60 80 / 20%);
}
</style>


