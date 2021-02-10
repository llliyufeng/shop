<template>
  <div class="nav">
    <div class="left"><slot name="left"></slot></div>
    <div class="center"><slot name="center"></slot></div>
    <div class="right"><slot name="right"></slot></div>
  </div>
</template>

<script>
  export default {
    name: "NavBar"
  }
</script>

<style scoped>
  .nav{
    display: flex;
    box-shadow: 0 1px 1px rgba(0,0,0,0.1);
    height: 44px;
    justify-content: center;
    align-items: center;
    text-align: center;
  }
  .left, .right{
    width: 60px;
    height: 100%;
    background: cornflowerblue;

  }
  .center{
    flex: 1;
  }
</style>