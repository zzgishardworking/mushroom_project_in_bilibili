<template>
  <div id="home">
    <nav-bar class="home-nav"><div slot="center">购物街</div></nav-bar>
    <homeSwiper :banners="banners"></homeSwiper>
    <home-recommend :recommends="recommends"></home-recommend>
  </div>
</template>

<script>
  import navBar from 'components/common/navbar/navBar'
  import homeSwiper from './childComps/HomeSwiper'
  import homeRecommend from './childComps/HomeRecommend'

  import {getHomeMultiData} from "network/home";


  export default {
    name: "home",
    components: {
      navBar,
      homeSwiper,
      homeRecommend
    },
    data() {
      return {
        banners: [],
        recommends:[]
      }
    },
    created() {
      getHomeMultiData().then(res => {
        this.banners = res.data.banner.list;
        this.recommends = res.data.recommend.list;
      })
    }
  }
</script>

<style scoped>
  .home-nav {
    background-color: var(--color-tint);
    color: #ffffff;

  }
</style>
