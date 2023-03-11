<template>
  <div class="lab" id="lab">
    <div class="labs-panel-title">
      <h2 class="labs-title">编程好工具，学习更轻松</h2>
      <p class="labs-title-info">选择适合你的编程神器</p>
    </div>
    <div class="labs-panel-info">
      <div class="labs-aside">
        <ul class="labs-nav-list">
          <li v-for="(info, index) in showLabs" :key="info.id" class="labs-nav-item"
              @mouseenter="changeBgc(info.hover_color, $event)"
              @mouseleave="changeBgc('#fff', $event)"
              @click="changeActive(info.id, index)"
              :class="activeId === info.id ? 'active' : ''"
          >
            <div class="labs-nav-item-icon" :style="{backgroundColor: activeId === info.id ? info.hover_color : '#fff'}"
            >
              <img :src="info.icon" class="labs-nav-item-icon-pic">
            </div>
            <div class="labs-nav-item-meta">
              <p class="labs-nav-item-title">{{info.name}}</p>
              <p class="labs-nav-item-info">{{info.tags}}</p>
            </div>
          </li>
        </ul>
        <div class="labs-nav-more" :class="prev ? 'up' : ''" @click="prev = !prev">
          <span></span>
        </div>
      </div>
      <div class="labs-main">
        <div class="labs-intro">
          <div class="labs-intro-figure">
            <p class="labs-intro-figure-info">{{lab[activeIndex].intro}}</p>
            <p class="labs-intro-figure-title">{{lab[activeIndex].name}}</p>
            <p class="labs-intro-figure-desc">{{lab[activeIndex].info}}</p>
            <div class="labs-intro-figure-ctrl">
              <div class="labs-intro-figure-ctrl-btn" @click="alert">立即创作</div>
              <div class="labs-intro-figure-ctrl-link" @click="alert">
                了解更多
                <span class="labs-intro-figure-ctrl-icon">&gt;</span>
              </div>
            </div>
          </div>
          <div class="labs-intro-cover">
            <img v-if="lab[activeIndex].show_type === 'image'" :src="lab[activeIndex].cover"
                 class="labs-intro-cover-pic">
            <video v-else :src="lab[activeIndex].video" autoplay="" playsinline="" webkit-playsinline="true"
                   mtt-playsinline="true" loop="" style="width: 100%; height: 100%;"></video>
          </div>
        </div>
        <div class="labs-example" v-if="lab[activeIndex].screenshot_title_1">
          <div class="labs-example-title">应用截图</div>
          <ul class="labs-example-list">
            <li class="labs-example-item" v-for="(item, index) in 3">
              <div class="labs-example-item-pic">
                <img :src="lab[activeIndex]['screenshot_' + [index + 1]]" class="labs-example-item-img">
              </div>
              <p class="labs-example-item-title">{{lab[activeIndex]['screenshot_title_' + [index + 1]]}}</p>
            </li>
          </ul>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
  export default {
    name: "Lab",
    data() {
      return {
        lab: [
          {
            "id": 1,
            "name": "创意实验室",
            "icon": "https://wuji-30130.sz.gfp.tencent-cloud.com/pics/20200306_g9ofq50ftsdcreative.png",
            "hover_color": "#FBE8C2",
            "tags": "6+岁,创造力,图形化",
            "intro": "像搭积木一样编程创作",
            "info": "让学编程和搭积木一样简单，有效帮助孩子形成编程思维，锻炼逻辑思维，轻松制作有趣有料的编程项目，发挥自己的无限创意。",
            "show_type": "video",
            "screenshot_1": "https://wuji-30130.sz.gfp.tencent-cloud.com/pics/20200318_03b5pb9xb9xp.png",
            "screenshot_title_1": "一起去郊游",
            "screenshot_2": "https://wuji-30130.sz.gfp.tencent-cloud.com/pics/20200318_2058cxoa8hv.png",
            "screenshot_title_2": "让贺卡动起来",
            "screenshot_3": "https://wuji-30130.sz.gfp.tencent-cloud.com/pics/20200318_1e0fz8k4etw.png",
            "screenshot_title_3": "下雪吧！",
            "video": "https://wuji-30130.sz.gfp.tencent-cloud.com/20200323_8htrkrqaeb52.mp4",
          },
          {
            "id": 2,
            "name": "Python实验室",
            "icon": "https://wuji-30130.sz.gfp.tencent-cloud.com/pics/20200306_7h0exzofi7tpython.png",
            "hover_color": "#C1DFFB",
            "tags": "7+岁,逻辑思维,Python",
            "intro": "通用易读的编程语言",
            "info": "从图形化编程到文本编程，从AI应用到硬件物联，首创带有舞台区的编辑模式，运用动画和声音制作游戏，全方面体会Python语言的乐趣。",
            "show_type": "video",
            "screenshot_1": "https://wuji-30130.sz.gfp.tencent-cloud.com/pics/20200318_7wbr2yla49.png",
            "screenshot_title_1": "画星星",
            "screenshot_2": "https://wuji-30130.sz.gfp.tencent-cloud.com/pics/20200318_5wctvliuxin.png",
            "screenshot_title_2": "AI智能（语音+图像）",
            "screenshot_3": "https://wuji-30130.sz.gfp.tencent-cloud.com/pics/20200318_5hedqxj4g5c.png",
            "screenshot_title_3": "计算生日",
            "video": "https://wuji-30130.sz.gfp.tencent-cloud.com/20200317_qrjirl2blsbpython.mp4",
          },
          {
            "id": 3,
            "name": "腾讯扣叮-编程第一课",
            "icon": require('../../assets/firstClassIcon.png'),
            "hover_color": "rgb(246, 202, 219)",
            "tags": "6-9岁编程启蒙计算思维",
            "intro": "专为6-9岁孩子定制的编程启蒙App",
            "info": "腾讯自研的游戏化编程启蒙APP，作为孩子的“编程第一课”，通过趣味的积木编程闯关，让孩子学习编程更简单、更有趣、更高效。",
            "show_type": "video",
            "screenshot_1": "https://wuji-30130.sz.gfp.tencent-cloud.com/pics/20210514_667b2qum87qimg1.png",
            "screenshot_title_1": "妙趣剧情，学习不枯燥",
            "screenshot_2": "https://wuji-30130.sz.gfp.tencent-cloud.com/pics/20210516_8hkhp06cbfq04.png",
            "screenshot_title_2": "编程闯关，探索编程奥秘",
            "screenshot_3": "https://wuji-30130.sz.gfp.tencent-cloud.com/pics/20210514_7xvlv329fmpimg3.png",
            "screenshot_title_3": "知识解锁，收获丰富趣味知识",
            "video": "https://wuji-30130.sz.gfp.tencent-cloud.com/20210516_rfqbytd62t.MP4",
          },
          {
            "id": 4,
            "name": "人工智能实验室",
            "icon": "https://wuji-30130.sz.gfp.tencent-cloud.com/pics/20200306_whgr206kz0sai.png",
            "hover_color": "#C1F4EC",
            "tags": "10+岁,前沿科技,走进AI",
            "intro": "算法模型，感受前沿科技",
            "info": "初学者直接应用简单的AI能力（拍照识花、语音识别、智能聊天等），体会AI的乐趣；高阶学习者参与常见算法模型的调参过程，学习AI的底层逻辑。",
            "show_type": "video",
            "screenshot_1": "https://wuji-30130.sz.gfp.tencent-cloud.com/pics/20200318_f32mm1mf6bu.png",
            "screenshot_title_1": "姿态侦测",
            "screenshot_2": "https://wuji-30130.sz.gfp.tencent-cloud.com/pics/20200318_zezz83b7i8s.png",
            "screenshot_title_2": "涂鸦",
            "screenshot_3": "https://wuji-30130.sz.gfp.tencent-cloud.com/pics/20200318_vqtfx8vb56t.png",
            "screenshot_title_3": "智能聊天",
            "video": "https://wuji-30130.sz.gfp.tencent-cloud.com/20200317_ojl6d4y4ciq.mp4",
          },
          {
            "id": 5,
            "name": "游戏实验室",
            "icon": "https://wuji-30130.sz.gfp.tencent-cloud.com/pics/20200306_16yws3wyo7hgame.png",
            "hover_color": "#DCC7FB",
            "tags": "6-8岁,创意游戏,零基础",
            "intro": "图形化编程，创意游戏闯关",
            "info": "积木块拼接而成的丰富多彩的创意游戏世界，零基础小朋友也可以通过图形化编程进行寻路闯关。",
            "show_type": "image",
            "cover": "https://wuji-30130.sz.gfp.tencent-cloud.com/pics/20200312_19kdyijatrlgeme.png",
          },
          {
            "id": 6,
            "name": "艺术(p5)实验室",
            "icon": "https://wuji-30130.sz.gfp.tencent-cloud.com/pics/20200306_otye6yv5nvart.png",
            "hover_color": "#F6CADB",
            "tags": "7+岁,艺术表达,数理知识",
            "intro": "用编程进行艺术表达",
            "info": "将编程与艺术、数学等STEAM多方面知识相结合，制作可视化的艺术案例，激发学生的想象力和创造力，帮助更好地学习理解数理知识。",
            "show_type": "image",
            "screenshot_1": "https://wuji-30130.sz.gfp.tencent-cloud.com/pics/20200319_tis672tlbb3.gif",
            "screenshot_title_1": "蒙德里安",
            "screenshot_2": "https://wuji-30130.sz.gfp.tencent-cloud.com/pics/20200319_kmojlnizag1.gif",
            "screenshot_title_2": "wavemaker",
            "screenshot_3": "https://wuji-30130.sz.gfp.tencent-cloud.com/pics/20200319_1zhg4pshyjkh2.gif",
            "screenshot_title_3": "recursice tree",
            "cover": "https://minigame.qq.com/common_manage/2862/detailIcon_b018f37d795c10314a403edfec04fb9a.png",
          },
          {
            "id": 7,
            "name": "硬件实验室",
            "icon": "https://wuji-30130.sz.gfp.tencent-cloud.com/pics/20200311_r7ymefinhg.png",
            "hover_color": "#C1F4EC",
            "tags": "6+岁,软硬结合,创客教育",
            "intro": "软硬件结合的编程体验",
            "info": "通过在线编程，控制Arduino、micro:bit、OpenAIE、CocoRobo等教育硬件，并同时支持积木和代码两种模式，体会软硬结合的编程学习。",
            "show_type": "image",
            "cover": "https://wuji-30130.sz.gfp.tencent-cloud.com/pics/20200312_nr2l8lzbpayingjian.png",
          },
          {
            "id": 8,
            "name": "JS实验室",
            "icon": "https://wuji-30130.sz.gfp.tencent-cloud.com/pics/20200311_8036tcku7o20200306_igf96a5gbzjs.png",
            "hover_color": "#FBE8C2",
            "tags": "7+岁,前端开发,JavaScript",
            "intro": "面向对象的Web语言",
            "info": "从积木命令到文本代码，从形状绘制到精灵动画，引导掌握计算机科学知识，从易到难感受JavaScript语言的魅力。",
            "show_type": "image",
            "screenshot_1": "https://wuji-30130.sz.gfp.tencent-cloud.com/pics/20200318_cp1j4hqdd.png",
            "screenshot_title_1": "彩虹旗",
            "screenshot_2": "https://wuji-30130.sz.gfp.tencent-cloud.com/pics/20200318_4cls7al5io1.png",
            "screenshot_title_2": "海底世界",
            "screenshot_3": "https://wuji-30130.sz.gfp.tencent-cloud.com/pics/20200318_jcw5u0z95y.png",
            "screenshot_title_3": "绘制大世界",
            "cover": "https://minigame.qq.com/common_manage/2862/detailIcon_8463cb6fdcb17afb9dc159cf5203786c.png",
          },
          {
            "id": 9,
            "name": "C实验室",
            "status": "show",
            "icon": "https://wuji-30130.sz.gfp.tencent-cloud.com/pics/20200306_2rzu5az9nsyc.png",
            "hover_color": "#C1DFFB",
            "tags": "12+岁,C语言,辅助竞赛",
            "intro": "面向过程的通用语言",
            "info": "纯文本编程，熟悉规范的开发流程；在线编译调试，不受运行环境影响；学习专业的C语言，为信息竞赛打下基础。",
            "show_type": "image",
            "cover": "https://wuji-30130.sz.gfp.tencent-cloud.com/pics/20200319_0k0mstzfvefc.png",
          }

        ],
        activeId: 0,
        activeIndex: 2,
        prev: false
      }
    },
    computed: {
      showLabs() {
        return this.prev ? this.lab.slice(0, 7) : this.lab.slice(2)
      }
    },
    created() {
      this.activeId = this.lab[2].id
    },
    methods: {
      changeActive(id, index) {
        this.activeId = id
        this.activeIndex = this.prev ? index : index + 2
      },
      changeBgc(color, e) {
        if (!e.target.classList.contains('active')) {
          e.target.children[0].style.backgroundColor = color
        }
      },
      alert() {
        window.alert('点击')
      }
    }
  }
</script>

<style scoped lang="scss">
  .lab {
    padding: 70px 0 80px;
  }

  /*标题*/
  .labs-panel-title {
    text-align: center;
    margin-bottom: 26px;
  }

  .labs-title {
    font-size: 40px;
    font-weight: 700;
    color: rgb(74, 89, 111);
    line-height: 60px;
  }

  .labs-title-info {
    font-size: 16px;
    color: rgba(74, 89, 111, 0.6);
    line-height: 24px;
  }

  .labs-panel-info {
    width: 1200px;
    display: flex;
    border-radius: 12px;
    overflow: hidden;
    background: #fff;
    margin: 0 auto;
  }

  /*左侧*/
  .labs-aside {
    width: 290px;
    background: #009cff;
    cursor: pointer;
  }

  .labs-nav-item {
    height: 82px;
    padding: 0 20px;
    transition: all 200ms;
    display: flex;
    align-items: center;
    border-bottom: 0.8px solid rgb(0, 144, 255);

    &:last-child {
      border-bottom: none;
    }

    &:hover {
      background: rgba(255, 255, 255, 0.1);
    }
  }

  .labs-nav-item:hover, .active {
    .labs-nav-item-icon {
      border-radius: 100%;
    }

    .labs-nav-item-icon-pic {
      transform: scale(0.9);
    }
  }

  .active {
    background: #fff;
    position: relative;

    &:hover {
      background: #fff;
    }

    .labs-nav-item-meta {
      color: #498ff6;
    }

    &::before {
      content: '';
      width: 4px;
      height: 82px;
      background: #0080ff;
      position: absolute;
      left: 0;
    }
  }

  .labs-nav-item-icon {
    width: 48px;
    height: 48px;
    background: #fff;
    border-radius: 12px;
    margin-right: 14px;
    display: flex;
    align-items: center;
    justify-content: center;
  }

  .labs-nav-item-meta {
    color: #fff;
  }

  .labs-nav-item-title {
    font-size: 18px;
  }

  .labs-nav-item-info {
    font-size: 12px;
  }

  .labs-nav-more {
    background: #0080ff;
    height: 26px;
    text-align: center;

    span {
      width: 0;
      height: 0;
      border-color: #fff transparent transparent transparent;
      border-style: solid;
      border-width: 8.4px 9.1px 0 9.1px;
      display: inline-block;
      border-radius: 4px;
    }
  }

  .up {
    span {
      border-color: transparent transparent #fff transparent;
      border-width: 0 9.1px 8.4px 9.1px;
    }
  }

  /*主面板*/
  .labs-main {
    margin-left: 50px;
    color: #4a596f;
  }

  /* 课程介绍*/
  .labs-intro {
    padding: 30px 0 20px;
    margin-bottom: 20px;
    display: flex;
    border-bottom: 0.8px solid rgba(74, 89, 111, 0.1);
  }

  .labs-intro-figure {
    width: 410px;
  }

  .labs-intro-figure-info {
    height: 30px;
    font-size: 16px;
    line-height: 24px;
    display: flex;
    align-items: center;
  }

  .labs-intro-figure-title {
    font-size: 24px;
    margin: 23px 0 12px;
  }

  .labs-intro-figure-desc {
    color: rgba(74, 89, 111, 0.6);
    height: 90px;
    line-height: 30px;
    overflow: hidden;
    text-overflow: ellipsis;
    display: -webkit-box;
    -webkit-box-orient: vertical;
    -webkit-line-clamp: 3;
  }

  .labs-intro-figure-ctrl {
    margin-top: 30px;
    display: flex;
    align-items: center;
  }

  .labs-intro-figure-ctrl-btn {
    width: 150px;
    height: 40px;
    line-height: 40px;
    background: #0080ff;
    border-radius: 20px;
    color: #fff;
    text-align: center;
    margin-right: 28px;
    cursor: pointer;
  }

  .labs-intro-figure-ctrl-link {
    font-size: 16px;
    line-height: 24px;
    cursor: pointer;

    &:hover {
      color: #009cff;
    }
  }

  .labs-intro-figure-ctrl-icon {
    margin-left: 6px;
  }

  .labs-intro-cover {
    width: 360px;
    height: 270px;
    overflow: hidden;
    margin-left: 40px;
    cursor: pointer;
  }

  .labs-intro-cover-pic {
    width: 360px;
    height: 270px;

    &:hover {
      transform: scale(1.03) translateZ(0);
    }
  }

  /*应用截图*/
  .labs-example-title {
    font-size: 18px;
    line-height: 27px;
    height: 34px;
  }

  .labs-example-list {
    list-style: none;
    display: flex;
    font-size: 16px;
    line-height: 24px;
    margin-top: 8px;
  }

  .labs-example-item {
    margin-right: 18px;
  }

  .labs-example-item-pic {
    width: 258px;
    height: 140px;
    border-radius: 4px;
    overflow: hidden;
    cursor: pointer;
  }

  .labs-example-item-img {
    width: 258px;
    height: 140px;

    &:hover {
      transform: scale(1.03) translateZ(0);
      transition: all 220ms;
    }
  }

  .labs-example-item-title {
    margin-top: 8px;
    cursor: pointer;

    &:hover {
      color: #0080ff;
    }
  }
</style>