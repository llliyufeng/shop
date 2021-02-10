<template>
  <div class="goodsItem">
    <img :src="goodsItem.show.img" alt="">
    <p>{{goodsItem.title}}</p>
    <div class="collect">
      <span class="price">￥{{goodsItem.price}}</span>
      <img src="../../../assets/img/home/collect.png" alt="">
      <span>{{goodsItem.sale}}</span>
    </div>
  </div>
</template>

<script>
  export default {
    name: "GoodsItem",
    props: {
      goodsItem: Object
    }
  }
</script>

<style scoped>
  .goodsItem{
    flex: 1;
    width: 47%;
    min-width: 47%;
    max-width: 47%;
    text-align: center;
    margin-bottom: 10px;
  }
  .goodsItem p{
    white-space: nowrap;
    overflow: hidden;
    font-size: 12px;
    text-overflow:ellipsis;
  }
  .goodsItem img{
    width: 100%;
  }
  .collect img {
    margin-top:1px;
    width: 16px;
    height: 16px;
    vertical-align: top;
  }
  .collect span {
    font-size: 14px;
    margin-right: 5px;
  }
  .price {
    color: cornflowerblue;
    font-weight: bold;
  }
</style>