<template>
  <div>
    <swiper :options="swiperOption">
      <!-- swiper-slides -->
      <!-- <slot name="swiper-img"></slot> -->
    <swiper-slide><img src="./shopcar-img/car_jinke@2x.png" alt=""></swiper-slide>
    <swiper-slide><img src="./shopcar-img/car_lanniao@2x.png" alt=""></swiper-slide>
    <swiper-slide><img src="./shopcar-img/car_jinke@2x.png" alt=""></swiper-slide>
    <swiper-slide><img src="./shopcar-img/car_jinke@2x.png" alt=""></swiper-slide>
      <div :class="{'swiper-pagination':bol}" slot="pagination"></div>
    </swiper>
  </div>
</template>

<script>
export default {
  props:{
    bol:{
      type:Boolean,
      default:true,
    },
    effect:{
      type:String,
      default:"slide"
    },
    delay:{
      type:Number,
      default:2000
    }
  },

  data() {
    return {
      swiperOption: {
        pagination: {
          el: ".swiper-pagination"
        },
         autoplay:{
           delay:this.delay,
           disableOnInteraction: false,
         },
         loop: true,
        effect:this.effect,
      }
    };
  },
  methods: {},
  components: {}
};
</script >

<style scoped lang='less'>
.swiper-container{
  width:100%;
    margin-top:0rem;
    height:1.13rem;
  .swiper-slide,.swiper-slide-duplicate {
    width:100%;
  img{
    width:3.75rem;
    height:100%;
  }
}
.swiper-pagination{
    top:-.1rem;
}
}
</style>
