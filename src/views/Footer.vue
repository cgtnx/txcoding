<template>
  <div class="footer">
    <div class="footer-nav">
      <div class="footer-logo"></div>
      <div class="footer-links footer-sitemap">
        <p class="footer-links-title">青少年编程</p>
        <div class="footer-links-wrapper">
          <ul class="footer-links-list">
            <li v-for="nav in navList.slice(0, 6)" :key="nav.id" class="footer-links-item" @click="alert">{{ nav.name
              }}
            </li>
          </ul>
          <ul class="footer-links-list">
            <li v-for="nav in navList.slice(6)" :key="nav.id" class="footer-links-item" @click="alert">{{ nav.name }}
            </li>
          </ul>
        </div>
      </div>
      <div class="footer-links">
        <p class="footer-links-title">友情链接</p>
        <div class="footer-links-wrapper">
          <ul class="footer-links-list">
            <li v-for="nav in friendlyLinks" :key="nav.id" class="footer-links-item" @click="alert">{{ nav.name }}</li>
          </ul>
        </div>
      </div>
      <div class="footer-qrcode">
        <div class="footer-qrcode-img">
          <img src="../assets/qrcode.png">
        </div>
        <p class="footer-qrcode-text">关注扣叮公众号</p>
        <p class="footer-qrcode-text">携手创造孩子未来</p>
      </div>
    </div>
    <div class="footer-copyright">
      <div class="footer-copyright-info">
        Copyright © 1998 - 2023 Tencent. All Rights Reserved. 腾讯公司 版权所有
      </div>
      <div class="footer-copyright-links">
        <span class="footer-copyright-text" @click="alert">服务协议</span>
        <span class="footer-copyright-line">|</span>
        <span class="footer-copyright-text" @click>隐私政策</span>
        <span class="footer-copyright-line">|</span>
        <span class="footer-copyright-text" @click>版权保护投诉指引</span>
      </div>
    </div>
  </div>
</template>

<script>
  export default {
    name: 'Footer',
    data() {
      return {
        navList: [
          {
            id: 1,
            name: '首页'
          },
          {
            id: 2,
            name: '实验室'
          },
          {
            id: 3,
            name: '课程'
          },
          {
            id: 4,
            name: '名师团'
          },
          {
            id: 5,
            name: '校园'
          },
          {
            id: 6,
            name: '社区'
          },
          {
            id: 7,
            name: '追梦营'
          },
          {
            id: 8,
            name: 'CodingDay'
          }

        ],
        friendlyLinks: [
          {
            id: 1,
            name: "腾讯游戏追梦计划"
          },
          {
            id: 2,
            name: "小鹅营地"
          },
          {
            id: 3,
            name: "智启学堂"
          },
          {
            id: 4,
            name: "腾讯工蜂"
          }
        ]
      };
    },
    methods: {
      alert() {
        window.alert('点击')
      }
    }
  };
</script>

<style lang="scss" scoped>
  .footer {
    width: 1200px;
    background: #fff;
    font-size: 14px;
    margin: 35px auto;
  }

  .footer-nav {
    display: flex;
    position: relative;
  }

  /*logo*/
  .footer-logo {
    width: 180px;
    height: 52px;
    background: url(data:image/png;base64,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) no-repeat;
  }

  /*链接*/
  .footer-sitemap {
    margin: 0 40px 0 180px;
  }

  .footer-links-title {
    font-size: 16px;
    color: rgba(74, 89, 111, 0.6);
    margin-bottom: 12px;
  }

  .footer-links-wrapper {
    display: flex;
  }

  .footer-links-list {
    list-style: none;
    min-width: 130px;
    margin-right: 40px;
  }

  .footer-links-item {
    color: #4a596f;
    line-height: 28px;
    cursor: pointer;

    &:hover {
      color: #2d81f6;
    }
  }

  /*二维码*/
  .footer-qrcode {
    position: absolute;
    text-align: center;
    top: 0;
    right: 0;
  }

  .footer-qrcode-img {
    border: 1px solid #eff3f8;
    border-radius: 4px;
    padding: 6px;
  }

  .footer-qrcode-text {
    color: rgba(74, 89, 111, 0.6);
  }

  /*版权信息*/
  .footer-copyright {
    height: 60px;
    display: flex;
    justify-content: space-between;
    align-items: center;
    border-top: 1px solid #eff3f8;
    margin-top: 30px;
    color: #4a596f;
  }

  .footer-copyright-text {
    cursor: pointer;

    &:hover {
      color: #2d81f6;
    }
  }

  .footer-copyright-line {
    color: rgba(74, 89, 111, 0.2);
    margin: 0 10px;
  }
</style>
