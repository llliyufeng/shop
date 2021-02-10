<template>
  <div>
    <swiper >
    <swiper-item v-for="item in banner" :key="item.arc">
      <a :href="item.link">
        <img :src="item.image" :alt="item.title">
      </a>
    </swiper-item>
    </swiper>
  </div>
</template>

<script>
  import {Swiper,SwiperItem} from '@/components/common/swiper'

  export default {
    name: "MainNavBar",
    components: {
      SwiperItem,
      Swiper
    },
    props: {
      banner: Array
    }
  }
</script>

<style scoped>

</style>