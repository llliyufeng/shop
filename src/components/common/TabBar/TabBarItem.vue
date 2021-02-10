<template>
  <div class="tabbaritem" @click="itemClick">
   <div v-if="!isActive"><slot name="item-icon"></slot></div>
    <div v-else><slot name="item-icon-active"></slot></div>
     <div :style="activeColor" ><slot  name="item-text"></slot></div>
  </div>
</template>

<script>
  export default {
    name: "TabBarItem",
    props: {
      path: String,
      color: {
        type: String,
        default: 'cornflowerblue'
      }
    },
    data() {
      return {
      }
    },
    computed: {
      isActive() {
        return this.$route.path === this.path
      },
      activeColor() {
        return this.isActive ? {color: this.color} : ''
      }
    },
    methods: {
      itemClick() {
        this.$router.push(this.path)
      },

    }
  }
</script>

<style scoped>
  .tabbaritem{
    flex: 1;
  }
  .tabbaritem img {
    padding-top: 3px;
    width: 24px;
    height: 24px;
  }

</style>