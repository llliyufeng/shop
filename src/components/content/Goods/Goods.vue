<template>
  <div class="goods">

      <goods-item  v-for="(item, index) in goods.list"
                   :key="index" class="goodsItem" :goodsItem="item"></goods-item>


  </div>
</template>

<script>
  import GoodsItem from "@/components/content/Goods/GoodsItem";
  export default {
    name: "Goods",
    props: {
      goods: Object
    },
    components: {
      GoodsItem
    },
    mounted() {
      console.log(this.goods)
    }
  }
</script>

<style scoped>
  .goods{
    width: 100%;
    display: flex;
    flex-wrap: wrap;
    justify-content: space-around;
    margin-top: 15px;
  }
  .goodsItem{
    width: 47%;
  }

</style>