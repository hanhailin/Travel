<template>
  <div class="icons">
    <swiper :options="swiperOption">
      <swiper-slide v-for="(page, index) of pages" :key="index">
        <div class="icon" v-for="item of page" :key="item.id">
          <div class="icon-img">
            <img class="icon-img-content" :src="item.imgUrl">
          </div>
          <p class="icon-desc">{{item.title}}</p>
        </div>
      </swiper-slide>
    </swiper>
  </div>
</template>

<script>
export default {
  name: 'HomeIcons',
  data () {
    return {
      swiperOption: {
        autoplay: false
      }
    }
  },
  props: {
    list: Array
  },
  computed: {
    pages: function () {
      const pages = []
      this.list.forEach((item, index) => {
        const page = Math.floor(index / 8)
        if (!pages[page]) {
          pages[page] = []
        }
        pages[page].push(item)
      })
      return pages
    }
  }
}
</script>

<style scoped lang="stylus">
@import '~styles/varibles.styl'
@import '~styles/mixins.styl'

.icons {
  height: 0;
  width: 100%;
  padding-bottom: 50%;
  overflow: hidden;

  .icon {
    position: relative;
    overflow: hidden;
    float: left;
    height: 0;
    width: 25%;
    padding-bottom: 25%;

    .icon-img {
      position: absolute;
      top: 0;
      box-sizing: border-box;
      padding: 0.1rem;
      left: 0;
      right: 0;
      bottom: 0.44rem;

      .icon-img-content {
        display: block;
        margin: 0 auto;
        height: 100%;
      }
    }
  }

  .icon-desc {
    position: absolute;
    bottom: 0;
    line-height: 0.44rem;
    height: 0.44rem;
    left: 0;
    right: 0;
    color: $darkTextColor;
    text-align: center;
    ellipsis();
  }
}
</style>
