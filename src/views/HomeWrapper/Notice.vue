<template>
  <div class="notice">
    <div class="notice-icon"></div>
    <div class="notice-info" v-for="(info, index) in notice" :key="info.id"
         :class="index === activeIndex ? 'active' : ''">
      <p class="notice-info-text" @click="alert">{{info.title}}</p>
      <div class="notice-info-tag" :class="info.tag">{{info.tag}}</div>
    </div>
  </div>
</template>

<script>
  export default {
    name: "Notice",
    data() {
      return {
        notice: [
          {
            "id": 1,
            "title": "追梦四年，以科技助力乡村教育普惠培养科技创新人才",
            "link": "https://mp.weixin.qq.com/s/EZGvlbcJyhZApVKGRaLJ7A",
            "tag": "new",
          },
          {
            "id": 2,
            "title": "追梦营移动站上线啦！！！",
            "link": "https://mp.weixin.qq.com/s/rLCGXSuCL_USVwAwFWa-_A",
            "tag": "hot",
          },
          {
            "id": 3,
            "title": "追梦导师，助梦成真",
            "link": "https://mp.weixin.qq.com/s/WORtzW_5DtjAOMFcK7vzKg",
            "tag": "hot",
          }
        ],
        activeIndex: 0
      }
    },
    mounted() {
      setInterval(this.changeActiveInfo, 5000)
    },
    methods: {
      changeActiveInfo() {
        this.activeIndex = this.activeIndex === this.notice.length - 1 ? 0 : this.activeIndex + 1;
      },
      alert() {
        window.alert('点击')
      }
    }
  }
</script>

<style scoped>
  .notice {
    width: 1200px;
    height: 70px;
    box-sizing: border-box;
    margin: 0 auto;
    background: #fff;
    border-radius: 0 0 12px 12px;
    padding: 0 28px;
    display: flex;
    align-items: center;
    position: relative;
  }

  .notice-icon {
    width: 138px;
    height: 22px;
    background-image: url(../../assets/moreIcon.png);
    background-position: 0 -40px;
  }

  .notice-info {
    display: flex;
    align-items: center;
    position: absolute;
    left: 166px;
    opacity: 0;
  }

  .active {
    opacity: 1;
  }

  .notice-info-text {
    margin: 0 10px 0 14px;
    color: #4a596f;
    cursor: pointer;
  }

  .notice-info-tag {
    width: 36px;
    height: 16px;
    border-radius: 8px 8px 8px 0;
    font-size: 12px;
    line-height: 16px;
    color: #fff;
    text-align: center;
  }

  .new {
    background: #68d8b8;
  }

  .hot {
    background: #EB676A;
  }
</style>