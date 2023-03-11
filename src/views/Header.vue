<template>
  <div class="header-container">
    <div class="logo">
      <div class="logo-plan" @click="alert"></div>
      <div class="logo-line"></div>
      <div class="logo-coding" @click="alert"></div>
    </div>
    <ul class="header-menus">
      <li v-for="menu in menus" :key="menu.id" class="header-menu-item" @click="alert">{{menu.name}}</li>
      <li @mouseenter="changeShowCompetitions" @mouseleave="changeShowCompetitions"
          class="header-menu-item showMoreContent"
          :class="showCompetitions ? 'hoverLi' : ''">
        赛事活动
        <div class="header-dropdown" v-show="showCompetitions">
          <ul class="header-dropdown-list">
            <li v-for="competition in competitions" :key="competition.id" class="header-dropdown-item" @click="alert">
              {{competition.name}}
            </li>
          </ul>
        </div>
      </li>
    </ul>
    <div class="header-toolbar">
      <div class="header-ideas">
        <div @mouseenter="changeShowIdeas" @mouseleave="changeShowIdeas" class="header-ideas-btn showMoreContent"
             :class="showIdeas ? 'hoverLi' : ''">
          立即创作
          <div class="header-dropdown" v-show="showIdeas">
            <ul class="header-dropdown-list">
              <li v-for="idea in ideas" :key="idea.id" class="header-dropdown-item" @click="alert">
                <i class="ec-header-icon" :class="`ec-header-icon-${idea.icon}`"></i>
                {{idea.name}}
              </li>
            </ul>
          </div>
        </div>
      </div>
      <div class="header-login" @click="alert">
        登录
      </div>
    </div>
  </div>
</template>

<script>

  export default {
    name: 'App',
    data() {
      return {
        menus: [
          {
            "id": 1,
            "name": "首页",
          },
          {
            "id": 2,
            "name": "实验室",
          },
          {
            "id": 3,
            "name": "课程",
          },
          {
            "id": 4,
            "name": "名师团",
          },
          {
            "id": 5,
            "name": "校园",
          },
          {
            "id": 6,
            "name": "社区",
          },
          {
            "id": 7,
            "name": "追梦营",
          },
          {
            "id": 8,
            "name": "CodingDay",
          }
        ],
        competitions: [
          {
            "id": 3,
            "name": "2023年NOC扣叮创意编程",
          },
          {
            "id": 6,
            "name": "2023年第五届腾讯青少年人工智能追梦营",
          }
        ],
        ideas: [
          {
            "id": 1,
            "name": "创意实验室",
            "icon": "creative-ide"
          },
          {
            "id": 2,
            "name": "Python实验室",
            "icon": "python-ide"
          },
          {
            "id": 3,
            "name": "3D实验室",
            "icon": "3d"
          },
          {
            "id": 4,
            "name": "人工智能实验室",
            "icon": "ai-ide"
          },
          {
            "id": 5,
            "name": "游戏实验室",
            "icon": "game-ide"
          },
          {
            "id": 6,
            "name": "艺术(p5)实验室",
            "icon": "p5-ide"
          },
          {
            "id": 7,
            "name": "硬件实验室",
            "icon": "hardware-ide"
          },
          {
            "id": 8,
            "name": "JS实验室",
            "icon": "js-ide"
          }
        ],
        showCompetitions: false,
        showIdeas: false
      }
    },
    methods: {
      changeShowCompetitions() {
        this.showCompetitions = !this.showCompetitions
      },
      changeShowIdeas() {
        this.showIdeas = !this.showIdeas
      },
      alert() {
        window.alert('点击')
      }
    }

  }
</script>

<style lang="scss">
  .header-container {
    display: flex;
    align-items: center;
    position: relative;
    min-width: 1200px;
  }

  .logo {
    display: flex;
    align-items: center;
    padding-left: 40px;
  }

  .logo-plan {
    width: 180px;
    height: 52px;
    background-size: 180px 52px;
    cursor: pointer;
    background-image: url(../assets/plan.png);
  }

  .logo-line {
    height: 25px;
    width: 1px;
    background: #d4dce8;
    margin: 0 10px;
  }

  .logo-coding {
    width: 133px;
    height: 57px;
    background-size: 133px 57px;
    cursor: pointer;
    background-image: url(../assets/coding.png);
  }

  .header-menus {
    list-style: none;
    display: flex;
    margin-left: 20px;

  }

  .header-menu-item {
    color: #4a596f;
    padding: 0 20px;
    line-height: 42px;
    transition: all 200ms;
    border-radius: 26px;
    cursor: pointer;

    &:last-child {
      color: #0080ff;
      @media screen and (max-width: 1400px) {
        display: none;
      }

      &:hover {
        background: none;
      }
    }

    &:hover {
      background: rgba(74, 89, 111, 0.1);
    }
  }

  .showMoreContent {
    &::after {
      width: 0;
      height: 0;
      content: '';
      border-width: 6px 4px 0 4px;
      border-color: #0080ff transparent transparent transparent;
      border-style: solid;
      display: inline-block;
      margin-left: 6px;
      transition: all 200ms;
      vertical-align: 2px;
    }
  }

  .hoverLi {
    position: relative;

    &::after {
      transform: rotate(180deg);
    }
  }

  /*下拉*/
  .header-dropdown {
    width: 214px;
    box-sizing: border-box;
    text-align: left;
    position: absolute;
    z-index: 2;
    background-color: #fff;
    box-shadow: 0 4px 20px rgb(77, 90, 109 / 40%);
    border-radius: 8px;
    top: 34px;
    left: 50px;
    margin-left: -89px;

    &::before {
      width: 0;
      height: 0;
      content: '';
      border-width: 0 10px 6px 10px;
      border-color: transparent transparent #fff transparent;
      border-style: solid;
      position: absolute;
      top: -5px;
      left: 50%;
      margin-left: -10px;
    }
  }

  .header-dropdown-list {
    list-style: none;
  }

  .header-dropdown-item {
    font-size: 14px;
    color: #4a596f;
    padding: 10px 20px;
    line-height: 1.5;

    &:hover {
      background: #f0f3f7;
      color: #009cff;
    }
  }

  .header-toolbar {
    display: flex;
    align-items: center;
    position: absolute;
    right: 40px;
  }

  /*立即创作*/
  .header-ideas-btn {
    width: 112px;
    font-size: 16px;
    line-height: 34px;
    text-align: center;
    color: #fff;
    background-color: #0080ff;
    border-radius: 17px;
    cursor: pointer;

    &:hover {
      background-color: #009cff;
    }

    .header-dropdown {
      width: 178px;
    }
  }

  .header-ideas-btn {
    &::after {
      border-color: #fff transparent transparent transparent;
    }
  }

  /*登录*/
  .header-login {
    line-height: 60px;
    margin-left: 20px;
    color: rgb(74, 89, 111);
    cursor: pointer;
  }

</style>
