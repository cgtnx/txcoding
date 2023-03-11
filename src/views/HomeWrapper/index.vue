<template>
  <div class="page">
    <Swiper/>
    <Notice/>
    <Lab ref="lab"/>
    <Sidebar v-show="sidebarShow" :show="0"/>
  </div>
</template>

<script>
  import Swiper from "./Swiper";
  import Notice from "./Notice";
  import Lab from "./Lab";
  import Sidebar from "./Sidebar";

  export default {
    name: 'HomeWrapper',
    components: {
      Swiper,
      Notice,
      Lab,
      Sidebar
    },
    data() {
      return {
        sidebarShow: false
      }
    },
    mounted() {
      window.addEventListener('scroll', this.labTop)
    },
    beforeDestroy() {
      window.removeEventListener('scroll', this.labTop)
    },
    methods: {
      labTop() {
        console.log(this.$refs.lab.$el.getBoundingClientRect().top)
        this.sidebarShow = Math.floor(this.$refs.lab.$el.getBoundingClientRect().top) <= 0;
      }
    }
  };
</script>

<style lang="scss" scoped>
  .page {
    background-color: rgb(239, 243, 248);
  }
</style>
