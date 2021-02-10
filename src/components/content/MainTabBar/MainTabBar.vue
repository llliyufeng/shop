<template>
  <div class="MainTabBar">

    <tab-bar-item path="/home" color="cornflowerblue">
      <template v-slot:item-icon>
        <img src="@/assets/img/home/home.svg" alt="">
      </template>
      <template v-slot:item-icon-active>
        <img src="@/assets/img/home/home-active.svg" alt="">
      </template>
      <template v-slot:item-text>
        首页
      </template>
    </tab-bar-item>
    <tab-bar-item path="/category" color="cornflowerblue">
      <template v-slot:item-icon>
        <img src="@/assets/img/category/category.svg" alt="">
      </template>
      <template v-slot:item-icon-active>
        <img src="@/assets/img/category/category-active.svg" alt="">
      </template>
      <template v-slot:item-text>
        分类
      </template>
    </tab-bar-item >
    <tab-bar-item  path="/cart" color="cornflowerblue">
      <template v-slot:item-icon>
        <img src="@/assets/img/cart/cart.svg" alt="">
      </template>
      <template v-slot:item-icon-active>
        <img src="@/assets/img/cart/cart-active.svg" alt="">
      </template>
      <template v-slot:item-text>
        购物车
      </template>
    </tab-bar-item>
    <tab-bar-item  path="/profile" color="cornflowerblue">
      <template v-slot:item-icon>
        <img src="@/assets/img/profile/profile.svg" alt="">
      </template>
      <template v-slot:item-icon-active>
        <img src="@/assets/img/profile/profile-active.svg" alt="">
      </template>
      <template v-slot:item-text>
        个人
      </template>
    </tab-bar-item>

  </div>
</template>

<script>
  import TabBarItem from "@/components/common/TabBar/TabBarItem";
  export default {
    name: "MainTabBar",
    data() {
      return {}
    },
    components: {
      TabBarItem
    }
  }
</script>

<style scoped>
  .MainTabBar{
    height: 49px;
    display:flex;
    position: fixed;
    left: 0;
    right: 0;
    bottom: 0;
    box-shadow: 0 -1px 1px rgba(0,0,0,.1);
    text-align: center;
    vertical-align: middle;
    padding-bottom: 2px;
    background: #fff;
  }
</style>