<template>
  <div class="shopcarbox">
    <side></side>
<top></top>
<banner></banner>
<router-link to="/Shaixuanb">
<local region="郑州" district='郑州动物动物园自助点' remark='该门店仅支持自助取车' class="shopone"></local>
</router-link>
<router-link to="/home">
<local region="郑州" district='二七广场自助点' remark='该门店仅支持自助取车' class="border-line"></local>
</router-link>
<time_></time_>
<router-link to="/Carlist">
<button_ text="立即选车"></button_>
</router-link>
<carlist></carlist>
  </div>
</template>

<script>
//引入头部
import top from "./hometop"
// 侧边栏
import side from "./sidebar"
//引入轮播图
import banner from "./homebanner"
//引入地区组件
import local from "./homearea"
//引入时间组件
import time_ from "./shopcartime"
//按钮组件
import button_ from "./button"
//车辆列表
import carlist from "./carlist"
 export default {
  data() {
    return {
    }
  },
  methods: {

  },
  components: {
      top,
      side,
      banner,
      local,
      time_,
      button_,
      carlist,
  }
}
</script >

<style scoped lang='less'>
.shopcarbox{
  padding-top:.45rem;
}
</style>
