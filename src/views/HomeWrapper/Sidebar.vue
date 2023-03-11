<template>
  <div class="sidebar">
    <ul class="sidebar-anchor-list">
      <li class="sidebar-anchor-item" :class="activeIndex === show ? 'active' : ''">
        <a href="#lab">
          <i class="sidebaricon sidebaricon-labs"></i>
          <p>实验室</p>
        </a>
      </li>
      <li class="sidebar-anchor-item" @click="goTop">
        <a href="javascript:void(0)">
          <i class="sidebaricon sidebaricon-top"></i>
          <p>回顶部</p>
        </a>
      </li>
    </ul>
  </div>
</template>

<script>
  export default {
    name: "Sidebar",
    props: {
      show: Number
    },
    data() {
      return {
        activeIndex: 0
      }
    },
    methods: {
      goTop() {
        window.scrollTo({
          top: 0,
          behavior: 'smooth'
        })
      }
    }
  }
</script>

<style scoped lang="scss">
  .sidebar {
    width: 60px;
    height: 136px;
    position: fixed;
    top: 146px;
    right: 25px;
    transition: all 200ms;
    border-radius: 8px;
    box-shadow: 0px 0px 4px rgb(74, 89, 111 / 20%);
    background: #fff;
    overflow: hidden;
    animation: bounce 300ms linear;

  }

  @keyframes bounce {
    0% {
      top: 500px;
    }
    100% {
      top: 146px;
    }
  }

  .sidebar-anchor-list {
    list-style: none;
  }

  .sidebar-anchor-item {
    font-size: 12px;
    line-height: 18px;
    color: #4a596f;
    border-bottom: 0.8px solid rgb(239, 243, 248);

    a {
      text-decoration: none;
      color: #4a596f;
    }

    a:hover, a:visited, a:link, a:active {
      color: #4a596f;
    }

    a {
      height: 68px;
      display: flex;
      flex-direction: column;
      justify-content: center;
      align-items: center;

      &:hover {
        color: #fff;
        background: #009cff;
      }
    }

    &:last-child {
      border-bottom: none;
    }
  }

  .active > a {
    color: #009cff !important;

    &:hover {
      color: #009cff !important;
      background: #fff;
    }
  }

  .sidebaricon {
    height: 18px;
    margin-bottom: 6px;
  }
</style>