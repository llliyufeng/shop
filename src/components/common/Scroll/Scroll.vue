<template>
  <div class="wrapper" ref="wrapper">
      <div class="content">
        <slot></slot>
      </div>

  </div>
</template>

<script>
  import BScroll from 'better-scroll'
  export default {
    name: "Scroll",
    data() {
      return {
        scroll: null,
      }
    },
    props: {
      probeType: Number,
      pullUpLoad: Boolean
    },
    mounted() {
      this.scroll = new BScroll(this.$refs.wrapper, {
        probeType: this.probeType,
        click: true,
        pullUpLoad: this.pullUpLoad,
        observeDOM: true
      })
      this.scroll.on('scroll', (position) => {
        this.$emit('getPosition',position)
      })
    },
    methods: {

      scrollPullUpLoad() {
        this.scroll.on('pullingUp', () => {
          this.$emit('pullingUp')
        })
      },
      finishPullUp() {
        this.scroll.finishPullUp()
      },
      backToTop(x, y, time) {
        this.scroll.scrollTo(x, y, time)
      }
    }

  }
</script>

<style scoped>
  .wrapper {
    height: calc(100% - 93px);
    position: absolute;
    left: 0;
    top: 0;
    overflow: hidden;
  }
</style>