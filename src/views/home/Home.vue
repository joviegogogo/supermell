<template>
  <div id="home">
    <nav-bar class="home-nav"><div slot="centent">购物街</div></nav-bar>
    <home-swiper :banner="banner"/>
    <recommend-view :recommend="recommend" />
    <feature-view/>
  </div>
</template>

<script>
import NavBar from "components/common/navbar/NavBar"
import HomeSwiper from "./childComps/HomeSwiper"
import RecommendView from "./childComps/RecommendView"
import FeatureView from "./childComps/FeatureView"

import {getHomeMultidata} from "network/home"


export default {
  name: "Home",
  components: {
    NavBar,
    HomeSwiper,
    RecommendView,
    FeatureView
  },
  data(){
    return{
      banner:[],  
      recommend:[]
    }
  },
  created() {
    //1,请求多个数据
    getHomeMultidata().then(res =>{
        console.log(res);
        this.banner = res.data.banner.list;
        this.recommend = res.data.recommend.list;
    })
  },
};
</script>

<style scoped>
#home{
 padding-top: 44px;  
}
.home-nav{
    background-color:var(--color-tint);
    color:#fff;

    position: fixed;
    left: 0;
    right: 0;
    top: 0;
    z-index: 9; 
}
</style>
