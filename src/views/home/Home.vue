<template>
<div id="home">
  <nav-bar class="home-nav"><div slot="center">购物街</div></nav-bar>
     <home-swiper :banners="banners"></home-swiper>
     <recommend-view :recommends="recommends"/>
  </div>
</template>

<script>
import NavBar from 'common/navbar/NavBar';
import HomeSwiper from './childComps/HomeSwiper';
import RecommendView from './childComps/RecommendView'


import {getHomeMultidata} from "network/home";

export default {
name: "Home",
components: {
  NavBar,
  HomeSwiper,
  RecommendView
},
data() {
  return {
    banners: [],
    recommends: []
  }
},
  created() {
    //1.请求多个数据
    getHomeMultidata().then(res => {
      console.log(res);
      //避免变量被垃圾回收
      this.banners = res.data.banner.list;
      this.recommends = res.data.recommend.list;

    })
  }

}
</script>

<style>

</style>