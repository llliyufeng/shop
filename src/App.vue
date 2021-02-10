<template>
  <div id="app">
    <keep-alive>
      <router-view></router-view>
    </keep-alive>
    <tab-bar class="tabBar"></tab-bar>
  </div>
</template>

<script>
  import TabBar from "@/components/common/TabBar/TabBar";

  export default {
  name: 'App',
  components: {
    TabBar
  },
  
}
</script>

<style>
@import "assets/css/base.css";

</style>
