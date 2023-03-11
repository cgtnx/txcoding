<template>
  <div class="swiper">
    <ul class="swiper-img-list">
      <li class="swiper-img-item">
        <img :src="swiperList[0].cover" class="swiper-img-pic">
      </li>
      <li v-for="(swiperItem, index) in swiperList"
          :key="swiperItem.id"
          class="swiper-img-item"
          :class="activeIndex === index ? 'active' : ''"
      >
        <img :src="swiperItem.cover" class="swiper-img-pic"/>
      </li>

    </ul>
    <div class="swiper-nav">
      <div class="swiper-nav-btn" @click="prevPic">
        <i class="prev iconhome iconhome-arrow"></i>
      </div>
      <ul class="swiper-nav-list">
        <li v-for="(swiperItem, index) in swiperList"
            :key="swiperItem.id"
            @click="nextPic(index)"
            class="swiper-nav-item"
            :class="activeIndex === index ? 'active' : ''"
        >
          {{ swiperItem.title }}
        </li>
      </ul>
      <div class="swiper-nav-btn" @click="nextPic()">
        <i class="iconhome iconhome-arrow"></i>
      </div>
    </div>
  </div>
</template>

<script>
  export default {
    name: 'Swiper',
    data() {
      return {
        swiperList: [
          {
            'id': 1,
            'title': '2023NOC扣叮创意编程',
            'cover': 'https://wuji-30130.sz.gfp.tencent-cloud.com/pics/20230303_t0ws1zgbobb.jpg'
          },
          {
            'id': 2,
            'title': '从边陲小镇到编程小镇',
            'cover': 'https://wuji-30130.sz.gfp.tencent-cloud.com/pics/20230103_5rzwqtvqv9y.png'
          },
          {
            'id': 3,
            'title': '编程与人工智能活动',
            'cover': 'https://wuji-30130.sz.gfp.tencent-cloud.com/pics/20221207_xgugst2gf7ra3.jpg'
          },
          {
            'id': 4,
            'title': '腾讯游戏年度故事片',
            'cover': 'https://wuji-30130.sz.gfp.tencent-cloud.com/pics/20221207_mslhp2hjkupa4.jpg'
          },
          {
            'id': 5,
            'title': '代码世界里的乡村教师',
            'cover': 'https://wuji-30130.sz.gfp.tencent-cloud.com/pics/20230103_hu6nv9iw39n.png'
          }
        ],
        activeIndex: 0,
        timer: 0
      };
    },
    mounted() {
      this.init();
    },
    methods: {
      init() {
        this.timer = setInterval(this.changeActivePic, 2000);
      },
      changeActivePic() {
        this.activeIndex = this.activeIndex === this.swiperList.length - 1 ? 0 : this.activeIndex + 1;
      },
      prevPic() {
        this.activeIndex = this.activeIndex === 0 ? this.swiperList.length - 1 : this.activeIndex - 1;
        clearInterval(this.timer);
        this.init();
      },
      nextPic(index) {
        index ? this.activeIndex = index : this.changeActivePic();
        clearInterval(this.timer);
        this.init();
      }
    }
  };
</script>

<style lang="scss" scoped>
  .swiper {
    width: 100%;
    min-width: 1200px;
    position: relative;
  }

  .swiper-img-list {
    .active {
      opacity: 1;
    }
  }

  .swiper-img-item {
    width: 100%;
    position: absolute;
    top: 0;
    opacity: 0;
    transition: all 500ms;

    &:first-child {
      position: relative;
      font-size: 0;
      opacity: 0;
    }
  }

  .swiper-img-pic {
    max-width: 100%;
    margin: 0 auto;
    object-fit: cover;
    object-position: 50% 50%;
  }

  .swiper-nav {
    width: 100%;
    max-width: 1200px;
    height: 50px;
    position: absolute;
    bottom: 0;
    left: 50%;
    transform: translate(-50%);
    z-index: 1;
    display: flex;
    justify-content: center;
    align-items: center;
    background: rgba(255, 255, 255, 0.8);
    font-size: 16px;
    border-radius: 12px 12px 0 0;
    overflow: hidden;
    cursor: pointer;
  }

  .swiper-nav-btn {
    width: 50px;
    line-height: 50px;
    color: rgba(74, 89, 111, 0.4);
    text-align: center;

    &:first-child {
      border-right: 1px solid rgba(255, 255, 255, 0.6);
    }

    &:hover {
      color: #009cff;
      background: #fff;
    }
  }

  .iconhome {
    content: "\e659";
  }

  .prev {
    display: inline-block;
    transform: rotate(180deg);
  }

  .swiper-nav-list {
    display: flex;
    flex: 1;
    list-style: none;

    .active {
      color: #009cff;

      &:after {
        height: 3px;
        background: #009cff;
      }
    }
  }

  .swiper-nav-item {
    flex: 1;
    line-height: 50px;
    text-align: center;
    color: #4a596f;
    transition: all 200ms;
    border-right: 1px solid rgba(255, 255, 255, 0.6);

    &:hover {
      color: #009cff;
    }
  }


  .swiper-nav-item, .swiper-nav-btn {
    position: relative;

    &:after {
      content: '';
      height: 6px;
      width: 100%;
      position: absolute;
      left: 0;
      bottom: 0;
      background: linear-gradient(rgba(255, 255, 255, 0), rgba(0, 0, 0, 0.1));
    }
  }

</style>
