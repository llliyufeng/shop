<template>
  <div class="tabControl" >
    <div class="tabControl-item" v-for="(item, index) in tabControl"
         @click="tabControlChange(index)"
         :key="index"
         :class="{active: index === currentIndex}">
      <span>{{item}}</span>
    </div>
  </div>

</template>

<script>
  export default {
    name: "TabControl",
    props: {
      tabControl: Array
    },
    data() {
      return {
        currentIndex: 0,
      }
    },
    methods: {
      tabControlChange(index) {
        this.currentIndex = index
        this.$emit('tabControlChange',index)
      }
    },
  }
</script>

<style scoped>
  .tabControl{
    display: flex;
    margin-top: 10px;
    text-align: center;
    font-size: 16px;
    font-weight: bold;


  }
  .tabControl-item {
    flex: 1;

  }
  .tabControl-item span{
    padding-bottom: 8px;

  }
  .active span{
    color:cornflowerblue;
    border-bottom: cornflowerblue 3px solid;
  }
</style>