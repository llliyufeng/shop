<template>
  <div>
    <nav-bar class="nav">
      <template v-slot:center>购物车</template>
    </nav-bar>
    <scroll class="content" ref="scroll"
            @pullingUp="pullingUp"
            @getPosition="getPosition"
            :probeType="3" :pullUpLoad="true">
      <main-roll-bar :banner="banner"></main-roll-bar>
      <recommend :recommend="recommend"></recommend>
      <feature :feature="feature"></feature>
      <tab-control :tabControl="tabControl" @tabControlChange="tabControlClick"></tab-control>
      <goods :goods="goods[currentType]" ></goods>
    </scroll>
    <back-top v-if="isBackTopShow" @click.native="backTop"></back-top>
  </div>
</template>

<script>
  import NavBar from '@/components/common/NavBar/NavBar'
  import MainRollBar from "@/views/home/MainRollBar/MainRollBar";
  import Recommend from "@/views/home/recommend/Recommend";
  import Feature from "@/views/home/feature/Feature";
  import TabControl from "@/components/content/TabControl/TabControl";
  import Goods from "@/components/content/Goods/Goods";
  import Scroll from "@/components/common/Scroll/Scroll";
  import BackTop from "@/views/home/BackTop/BackTop";


  import {getHomeMultidata, getHomeData} from '@/network/home'
  export default {
    name: "Home",
    data() {
      return {
        banner: [],
        recommend: [],
        feature: [],
        tabControl: ['流行','新款','精选'],
        goods: {
          'pop': {page: 0, list: []},
          'new': {page: 0, list: []},
          'sell': {page: 0, list: []}
        },
        currentType: 'pop',
        isBackTopShow: 'false'
      }
    },
    components: {
      NavBar,
      MainRollBar,
      Recommend,
      Feature,
      TabControl,
      Goods,
      Scroll,
      BackTop
    },
    created() {
      this.getHomeMultidata()
      this.getHomeData('pop')
      this.getHomeData('new')
      this.getHomeData('sell')

    },
    mounted(){
      this.$refs.scroll.scrollPullUpLoad()
    },
    methods: {
      getHomeMultidata() {
        getHomeMultidata().then(res => {
          this.banner = res.data.data.banner.list
          this.recommend = res.data.data.recommend.list
          this.feature = res.data.data.keywords.list
        })
      },
      getHomeData(type) {
        const page = this.goods[type].page+1
        getHomeData(type, page).then(res => {
          this.goods[type].list.push(...res.data.data.list)
          this.goods[type].page += 1
          this.$refs.scroll.finishPullUp()
        })

      },
      pullingUp() {
        this.getHomeData(this.currentType)
        this.$refs.scroll.scroll.refresh()
      },
      tabControlClick(index) {
        switch (index) {
          case 0 :
            this.currentType = 'pop'
            break
          case 1 :
            this.currentType = 'new'
            break
          case 2 :
            this.currentType = 'sell'
        }
      },
      backTop() {
        this.$refs.scroll.backToTop(0,0,500)
      },
      getPosition(position) {
        this.isBackTopShow = (-position.y) > 1000

      }
    },


  }
</script>

<style scoped>
  .nav{
    background-color: cornflowerblue;
    font-size: 20px;
    font-weight: bold;
    color: white;
    letter-spacing: 15px;
  }
  .content {
    margin-top: 44px;
    width: 100%;
    height: calc(100% - 93px);
    /*overflow: hidden;*/
    margin-bottom: 48px;
  }

</style>