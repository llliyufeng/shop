<template>
  <div class="recommend">
    <div class="recommend-item" v-for="item in recommend" :key="item.acm">
        <img :src="item.image" :alt="item.title">
        <span>{{item.title}}</span>
    </div>
  </div>
</template>

<script>
  export default {
    name: "Recommend",
    props: {
      recommend: {
        type: Array
      }
    },
    mounted(){
    },
  }
</script>

<style scoped>
  .recommend{
    display: flex;
    text-align: center;
    padding: 15px 0px 15px;
    border-bottom: 10px solid rgba(0,0,150,.08);

  }
  .recommend-item {
    flex: 1;
  }
  .recommend-item img {
    width: 65px;
    height: 65px;
  }
  .recommend-item span{
    display: block;
    color: steelblue;
    font-weight: 400;
    font-size: 16px;
  }
</style>