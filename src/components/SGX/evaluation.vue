<template>
  <div class="evaluation_bigbox">
    <Public>
      <div class="big-box" slot="heade">
        <div class="header">
          <router-link to="/Paysuccess" class="back">
            <!-- <img src="../../../static/SGXimg/icon_back@2x.png" alt="" /> -->
          </router-link>
          <span class="head">评价</span>
          <span class="next"></span>
        </div>
      </div>
    </Public>

    <ul class="list">
      <li class="cardetails animated bounceInUp delay faster">
        <div class="cardetails_one_div">
          <span class="cartitle">车辆信息</span>
          <div class="car_information">
            <span>丰田汉兰达</span>
            <span class="car_information_spantwo">豫A88888</span>
          </div>
        </div>
        <div class="cardetails_two_div">
            <p class="cardetails_two_div_one_p"> <span>订单号</span><span>{{abc}}</span></p>
            <p class="cardetails_two_div_two_p"><span>时间</span><span>2015-5-2964654655</span></p>
        </div>
      </li>
      <p class="car_stores animated bounceInUp delay1 faster">取车门店</p>
      <li class="stores animated bounceInUp delay1 faster">
        <div class="stores_one_div"> 
          <textarea class="stores_one_div_textarea" placeholder="对于这次的车辆使用整个过程，您有什么意见或者建议吗？ 很期待您的意见哦!" cols=26>

          </textarea>
        </div>
        <div class="stores_two_div">
          <div class="upimg">
             <input accept="image/*" name="img" id="upload_file" type="file" @change="update" webkitRelativePath multiple>
             
          </div>
          <div class="image">
            <img :src='ImgUrl'alt="" id="imged">
          </div>
         
        </div>
        <div class="stores_three_div">
          <p class="stores_three_div_one_p">
            <span>服务态度:</span>
           <ul class="star">
              <li v-for="(itemClass,index) in itemClasses" :class="itemClass" class="star-item" @click="stars(index)" track-by="index"></li><!--性能优化 track-by 数据不改变时不会重新渲染-->
            </ul>
          </p>
          <p class="stores_three_div_one_p">
            <span>服务态度:</span>
           <ul class="star">
              <li v-for="(itemClass,index) in itemClasses" :class="itemClass" class="star-item" @click="stars1(index)" track-by="index"></li><!--性能优化 track-by 数据不改变时不会重新渲染-->
            </ul>
          </p>
          <p class="stores_three_div_two_p"></p>
        </div>
      </li>
      <p class="car_stores animated bounceInUp delay2 faster">取车门店</p>
      <li class="Payli animated bounceInUp delay2 faster">
         <div class="stores_one_div"> 
          <textarea class="stores_one_div_textarea" placeholder="对于这次的车辆使用整个过程，您有什么意见或者建议吗？ 很期待您的意见哦!" cols=26>

          </textarea>
        </div>
        <div class="stores_two_div">
          <div>
            <div class="upimg">
            
            </div>
          <p>点击上传图片</p>
          </div>
          
        </div>
        <div class="stores_three_div">
          <p class="stores_three_div_one_p">
            <span>服务态度:</span>
           <ul class="star">
              <li v-for="(itemClass,index) in itemClasses" :class="itemClass" class="star-item" @click="stars(index)" track-by="index"></li><!--性能优化 track-by 数据不改变时不会重新渲染-->
            </ul>
          </p>
          <p class="stores_three_div_one_p">
            <span>服务态度:</span>
           <ul class="star">
              <li v-for="(itemClass,index) in itemClasses" :class="itemClass" class="star-item" @click="stars1(index)" track-by="index"></li><!--性能优化 track-by 数据不改变时不会重新渲染-->
            </ul>
          </p>
          <p class="stores_three_div_two_p"></p>
        </div>
      </li>
      <li class="published animated bounceInUp delay3 faster">
        <div><span></span><span>匿名发表评论</span></div>
        <div @click="fn()">
          <router-link to="" class="router_" >发表评论</router-link>
          </div>
      </li>
    </ul>
  </div>
</template>

<script>
import Public from "./public-header";

// import Uploader from "./index";
export default {
  data() {
    return {
      score:5,
      score1:5,
       fileList: [],
      width:0.6+"rem",
      // height:0.55+"rem"
      abc:"13213213",
      ImgUrl:''
    };
  },
 
 computed:{ //计算属性
              itemClasses(){
              let result = []; // 返回的是一个数组,用来遍历输出星星
              let score = Math.floor(this.score * 2 ) / 2; // 计算所有星星的数量
              let hasDecimal = score % 1 !== 0; // 非整数星星判断
              let integer = Math.floor(score); // 整数星星判断
              for(let i=0;i<integer;i++){ // 整数星星使用on
              result.push("on"); // 一个整数星星就push一个CLS_ON到数组
              }
              if(hasDecimal){ // 非整数星星使用half
              result.push("half"); // 类似

              } 
              while(result.length < 5){// 余下的用无星星补全,使用off
              result.push("off");
              }
              return result;
              }
              },
                methods:{
              stars:function(index){
              this.score = index;
              console.log(index)
              },
              stars1:function(index){
              this.score1 = index;
              console.log(index)
                },
                fn(){
                  this.$router.push({
                    path:'/Paysuccess',
                    query:{
                      p:this.abc,
                    }
                  })
                },
                
                update (e) { 
                 // 上传照片
              
   var self = this
   let file = e.target.files[0];
   console.log(file);
  //  this.imgs=file;
   /* eslint-disable no-undef */
   let param = new FormData() // 创建form对象
   param.append('file', file, file.name) // 通过append向form对象添加数据
   param.append('chunk', '0') // 添加form表单中其他数据
   console.log(param.get('file')) // FormData私有类对象，访问不到，可以通过get判断值是否传进去
   let config = {
    headers: {'Content-Type': 'multipart/form-data'}
   }
  //  const instance=this.axios.create({
  //    withCredentials:true
  //  })
  // instance.post('http://172.25.1.194:8080/', param, config)
  //   .then(response => {
  //    if (response.data.code === 0) {
  //     self.ImgUrl = response.data.data
  //    }
  //    console.log(response.data)
  //   })

      var imgFile = file;
        var fr = new FileReader();
        fr.onload = function () {
          document.getElementById('imged').src = fr;
        };
          fr.readAsDataURL(imgFile);
        console.log(imgFile);
  },
//   great: function () {
//     document.getElementById('upload_file').onchange = function () {
      
//     }
// }      
                
              
  }
  ,
  components: {
    Public,
    // Uploader
  },
  mounted(){
    //  this.great();
}
}
</script>

<style scoped lang='less'>
*{
    font-family:'PingFang-SC-Bold';
}
.align_items {
  display: flex;
  align-items: center;
}
.flex-column {
  display: flex;
  flex-direction: column;
}
.font14{
  height: 0.14rem;
  font-size: 0.14rem;
  font-weight: bold;
  color: #333333;
}
.font13{
  height: 0.13rem;
  font-size: 0.13rem;
  font-weight: bold;
  color: #333333;
}
.font12{
  font-size:0.12rem;
  color:#999999
}
.cardetails_two_div_one_p_span{
   .font13();
                height:0.13rem;
                display:inline-block;
                margin-left:0.12rem;
}
.next {
  background: url("../../../static/SGXimg/wenhao.png") no-repeat center center;
  background-size: 0.18rem 0.18rem;
}
/deep/ #upload_file{
       width:100%;
       height:100%;
        _height: auto;
        opacity: 0;
        filter: alpha(opacity=0);
        -ms-filter: "alpha(opacity=0)";
        background-color: #ccc;
        }


.evaluation_bigbox {
  width: 100%;
  // height: 100%;
  background-color: #f7f8fa;
  .list {
    height:100%;
    padding: 0.23rem 0.16rem 0.16rem 0.16rem;
    li {
    //   margin-top: 0.12rem;
      background-color: white;
      border-radius: 0.1rem;
      box-sizing: border-box;
      animation-duration: 0.8s;
    }
    .cardetails {
        height:0.73rem;
      .flex-column();
      background-color:#f7f8fa;
      .cardetails_one_div {
            flex:1;
            display: flex;
            justify-content: space-between;
            border-bottom:1px solid #ccc;
        .cartitle{
            .font14();
        }
        .car_information{
           
                .font13();
                .car_information_spantwo{
                  margin-left:0.24rem;
                  .font12();
                }
              
            
            
        }
      }
      .cardetails_two_div{
          flex:1.5;
          font-size:0;
          text-align:left;
          .cardetails_two_div_one_p{
          
              margin-top:0.12rem;
              
              &>span:nth-child(1){
                .cardetails_two_div_one_p_span();
                color:#999999;
              }
              &>span:nth-child(2){
               .cardetails_two_div_one_p_span();
                // color:#999999;
              }
            
          }
          .cardetails_two_div_two_p{
            margin-top:0.07rem;
              &>span:nth-child(1){
                .cardetails_two_div_one_p_span();
                color:#999999;
              }
              &>span:nth-child(2){
               .cardetails_two_div_one_p_span();
               margin-left:0.24rem;
                // color:#999999;
              }
          }
      }
    }
    .stores{
      height:2.27rem;
      // padding:0.17rem 0 0.11rem 0.12rem;
      .flex-column();
      .stores_one_div{
        flex:1;
        display:flex;
         padding:0.17rem 0 0 0.12rem;
         box-sizing: border-box;
        .stores_one_div_textarea{
          flex:1;
          .font12();
          // width:100%;
          // height:0.6773rem;
        
         
        }
      }
      .stores_two_div{
        flex:1.15;
        height:0.76rem;
        font-size: 0; position: relative;
        .upimg{
          width:0.6rem;
          height:0.55rem;
          background-color:#F0F1F5;
          z-index:3;
          position: absolute;
          left: 0.13rem;
          top: 0;
          width:0.6rem;       
          height: 0.55rem;
          .image{
            width:0.6rem;
            height:0.55rem;
            position:absolute;
            top:0;
            left:0.75rem;
            img{
              width:100%;
              height:100%;
            }
          }
        }
       
      }
      .stores_three_div{
        flex:1.2;
        .stores_three_div_one_p{
          display:flex;
          // align-items: center;
          height:0.17rem;
          margin-top:0.12rem;
          &>span:nth-child(1){
            .font13();
            margin-left:1.1rem;
          }



                .evaStar{
          float:right;
          // padding-top: .34rem;
          }
          .star{
          font-size: 0;
          }
          .star-item{
          display: inline-block;
          background-repeat: no-repeat;
          width: .19rem;
          height: .17rem;
          margin-left: .12rem;
          background-size: 100%;
          }
          .star-item.on{
          background-image: url(../../../static/SGXimg/icon_xing_n@2x.png);
          }
          .star-item.half{
          background-image: url(../../../static/SGXimg/icon_xing@2x.png);
          }
          .star-item.off{
          background-image: url(../../../static/SGXimg/icon_xing@2x.png);
          }
        }
      }
    }
  .Payli{
    height:2.27rem;
      // padding:0.17rem 0 0.11rem 0.12rem;
      .flex-column();
      .stores_one_div{
        flex:1;
        display:flex;
         padding:0.17rem 0 0 0.12rem;
         box-sizing: border-box;
        .stores_one_div_textarea{
          flex:1;
          .font12();
          // width:100%;
          // height:0.6773rem;
        
         
        }
      }
      .stores_two_div{
        flex:1.15;
        div{
         
        
           .upimg{
          width:0.6rem;
          height:0.55rem;
          background: url('../../../static/SGXimg/upimg.png')no-repeat center center;
          background-color:#F0F1F5;
          background-size: 0.29rem 0.24rem;
           margin-left:0.12rem;
         
         
        } p{
            .font12();
             margin:0.05rem 0 0 0.12rem;
             text-align:left;
          }
        }
       
      }
      .stores_three_div{
        flex:1.2;
        .stores_three_div_one_p{
          display:flex;
          // align-items: center;
          height:0.17rem;
          margin-top:0.12rem;
          &>span:nth-child(1){
            .font13();
            margin-left:1.1rem;
          }



                .evaStar{
          float:right;
          // padding-top: .34rem;
          }
          .star{
          font-size: 0;
          }
          .star-item{
          display: inline-block;
          background-repeat: no-repeat;
          width: .19rem;
          height: .17rem;
          margin-left: .12rem;
          background-size: 100%;
          }
          .star-item.on{
          background-image: url(../../../static/SGXimg/icon_xing_n@2x.png);
          }
          .star-item.half{
          background-image: url(../../../static/SGXimg/icon_xing@2x.png);
          }
          .star-item.off{
          background-image: url(../../../static/SGXimg/icon_xing@2x.png);
          }
        }
      }
  }
  .published{
    height:0.34rem;
    background-color:#F9C307;
    display: flex;
    // align-items:center;
    border-radius:0.2rem;
    margin-top:0.16rem;
    div{
      flex:1;
      justify-content: center;
      display: flex;
      align-items:center;
    }
    &>div:nth-child(2){
      font-size:0.16rem;
    
      font-weight: bold;
      .router_{
          color:white;
      }
    }
    &>div:nth-child(1){
   
      font-size:0.12rem;
      color:white;
      font-weight: bold;
    }
  }
    .car_stores{
      .font13();
      text-align:center;
       animation-duration: 0.8s;
      margin:0.12rem 0;
    }
  }
}
 .delay {
    animation-delay: 0.08s;
  }
  .delay1 {
    animation-delay: 0.15s;
  }
  .delay2 {
    animation-delay: 0.22s;
  }
  .delay3 {
    animation-delay: 0.29s;
  }
</style>
