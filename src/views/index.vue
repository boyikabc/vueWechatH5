<template>
  <div class="box">
    <vue-drawer-layout :drawer-width="230" ref="drawerLayout" @mask-click="closeMenu()">
      <div class="drawer" slot="drawer">
        <div>菜单栏</div>
      </div>
      <div class="content" slot="content">
        <van-button type="primary" @click="openMenu()">打开菜单栏</van-button>
      </div>
    </vue-drawer-layout>
  </div>
</template>

<script>
import { getCarouselList } from "../axios/request";
export default {
  data() {
    return {};
  },

  mounted() {},

  methods: {
    async getApi() {
      const res = await getCarouselList({ page: 1, limit: 10 });
      if (res.status == 1) {
        this.bannerList = res.data;
      }
    },
    openMenu() {
      this.$refs.drawerLayout.toggle();
    },
    closeMenu() {
      this.$refs.drawerLayout.toggle(false);
    },
  },
};
</script>
<style lang="less" scoped>
.drawer {
  width: 100%;
  height: 100%;
  background: #fff;
}
</style>
