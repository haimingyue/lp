<template>
  <div class="home" v-loading="loading">
    <swiper id="swiperBox" v-bind:options="swiperOption" ref="mySwiper">
      <swiper-slide class="swiper-slide slide-one">
        <div class="page">
          <h3>普石彩普</h3>
          <p>Pu Shi</p>
        </div>
        <p class="slogan">地面材料的第一选择</p>
      </swiper-slide>
      <swiper-slide class="swiper-slide slide-two">
        <div class="page">
          <h3>经典案例</h3>
          <p>Suecessful Cass</p>
        </div>
        <ul class="case-item">
          <li
            v-for="(item,index) in caseList"
            :key="index"
            v-lazy:background-image="item.Img"
          >
            <router-link
              class="text-decoration"
              :to="{ name: 'casedetails', params: { id: item.Id }}"
            >
              <div class="case-item-hover">
                <p class="hover-title">{{item.Title}}</p>
                <div class="bottom"></div>
                <div class="more">
                  <span>MORE</span>
                </div>
              </div>
            </router-link>
          </li>
        </ul>
      </swiper-slide>
      <!-- <swiper-slide class="swiper-slide slide-three">
        <div class="page">
          <h3>最新资讯</h3>
          <p>Latest News</p>
        </div>
        <div class="news-content">
          <div class="news-content-item" v-for="(news,i) in newsList" :key="i">
            <div :style="'order: '+ (i%2==0 ? 1: 3)">
              <router-link
                class="text-decoration"
                :to="{ name: 'newsdetails', params: { id: news.Id }}"
              >
                <div class="item-img" v-lazy:background-image="imgserver + news.Img"></div>
              </router-link>
            </div>
            <div style="order: 2">
              <el-divider>
                <i class="el-icon-apple"></i>
              </el-divider>
            </div>
            <div class="item-content" :style="'order: '+ (i%2==0 ? 3: 1)">
              <h3>{{news.Title}}</h3>
              <p>{{news.Content}}</p>
              <span>{{news.CreateTime}}</span>
            </div>
          </div>
        </div>
      </swiper-slide> -->
    </swiper>
  </div>
</template>
 
<script>
import { swiper, swiperSlide } from "vue-awesome-swiper";
export default {
  name: "HelloWorld",
  components: {
    swiper,
    swiperSlide
  },
  data() {
    return {
      loading: true,
      caseList: [],
      newsList: [],
      swiperOption: {
        notNextTick: true, //notNextTick是一个组件自有属性，如果notNextTick设置为true，组件则不会通过NextTick来实例化swiper，也就意味着你可以在第一时间获取到swiper对象，假如你需要刚加载遍使用获取swiper对象来做什么事，那么这个属性一定要是true
        direction: "vertical", //水平方向移动
        grabCursor: true, //鼠标覆盖Swiper时指针会变成手掌形状，拖动时指针会变成抓手形状
        setWrapperSize: true, //Swiper使用flexbox布局(display: flex)，开启这个设定会在Wrapper上添加等于slides相加的宽或高，在对flexbox布局的支持不是很好的浏览器中可能需要用到。
        autoHeight: true, //自动高度。设置为true时，wrapper和container会随着当前slide的高度而发生变化
        slidesPerView: 1, //设置slider容器能够同时显示的slides数量(carousel模式)。可以设置为数字（可为小数，小数不可loop），或者 'auto'则自动根据slides的宽度来设定数量。loop模式下如果设置为'auto'还需要设置另外一个参数loopedSlides。
        mousewheel: true, //开启鼠标滚轮控制Swiper切换。可设置鼠标选项，默认值false
        mousewheelControl: true, //同上
        height: window.innerHeight - 60, // 高度设置，占满设备高度
        resistanceRatio: 0, //抵抗率。边缘抵抗力的大小比例。值越小抵抗越大越难将slide拖离边缘，0时完全无法拖离。本业务需要
        observeParents: true, //将observe应用于Swiper的父元素。当Swiper的父元素变化时，例如window.resize，Swiper更新

        // 如果自行设计了插件，那么插件的一些配置相关参数，也应该出现在这个对象中，如下debugger
        //debugger: true,

        // swiper的各种回调函数也可以出现在这个对象中，和swiper官方一样
        on: {
          //监听滑动切换事件，返回swiper对象
          // slideChange: () => {
          //   let swiper = this.$refs.mySwiper.swiper;
          //   //console.log(swiper.activeIndex); //滑动打印当前索引
          //   if (swiper.activeIndex === this.list.length - 1) {
          //     //到最后一个加载更多数据
          //     let newList = [];
          //     let listLength = this.list.length;
          //     for (let i = 0; i < 10; i++) {
          //       newList.push(listLength + i);
          //     }
          //     this.list = this.list.concat(newList);
          //   }
          // }
        }
      }
    };
  },
  created() {},
  // 如果你需要得到当前的swiper对象来做一些事情，你可以像下面这样定义一个方法属性来获取当前的swiper对象，同时notNextTick必须为true
  computed: {
    swiper() {
      return this.$refs.mySwiper.swiper;
    }
  },
  mounted() {
    // this.$http
    //   .all([
    //     this.$http.get("Cases/GetCasesAll"),
    //     this.$http.get(`News?type=1&num=3`)
    //   ])
    //   .then(
    //     this.$http.spread((responseCases, responseNews) => {
    //       console.log('responseCases.data', JSON.stringify(responseCases.data))
    //       console.log('responseCases.data', JSON.stringify(responseNews.data))
    //       this.caseList = responseCases.data;
    //       this.newsList = responseNews.data;
    //       this.loading = false;
    //     })
    //   );
      this.caseList = 
        [
          {
            "Id": 29,
            "Img": require('../assets/img/ps/pscp_img0.jpg'),
            "Title": "上海市公共安全教育实训基地项目位",
            "Content": "位于上海市青浦区沪青平公路6888号“东方绿舟”东南 角，四界范围为：东临城市河道，南至沪青平公路，西界绿湖路，北靠现有的东方绿舟停机 坪。项目用地面积65048平方米（以实测为准），新建总建筑面积约为26467平方米（地上 23500平方米，地下2967平方米）",
            "Del": null,
            "CreateTime": "2020-06-05T21:12:45.387"
          }, {
            "Id": 28,
            "Img": require('../assets/img/ps/pscp_img1.jpg'),
            "Title": "高端装备用特种电缆检测评估服务基地",
            "Content": "高端装备用特种电缆检测评估服务基地建设 一期工程位于上海市宝山区山连路558号， 项目建筑面积为19324.03平方米（地上建 筑面积为15446.74平方米，地下建筑面积\n为3877.29平方米）。",
            "Del": null,
            "CreateTime": "2020-06-05T21:05:45.157"
          }, {
            "Id": 27,
            "Img": require('../assets/img/ps/pscp_img2.jpg'),
            "Title": "中国移动上海公司临港数据中心",
            "Content": "上海移动临港IDC研发与产业化基地项目一 期数据中心2#机楼微模块机房配套工程",
            "Del": null,
            "CreateTime": "2020-06-05T21:02:05.567"
          }, {
            "Id": 26,
            "Img": require('../assets/img/ps/pscp_img3.jpg'),
            "Title": "上海合作组织国际司法交流培训基地项目",
            "Content": "上海合作组织国际司法交流合作培训基地（上海政法学院）工程位于松江区泗陈公路5488号\n上海政法学院东南部，项目用地面积66125平方米（以实测为准），新建总建筑面积约为 24976平方米，其中地上建筑面积为22476平方米，地下建筑面积约为2500平方米。",
            "Del": null,
            "CreateTime": "2020-06-05T20:58:05.57"
          }
        ]
      // this.newsList = [{"Id":19,"Title":"热烈祝贺上海科建获得上海市工程监理资质","Img":"/imagestore/2018/0917/98c71315-86dc-4c99-b973-c89136bd8885.jpg","Type":1,"Content":"热烈祝贺上海科建工程管理股份有限公司获得上海市工程监理资质证书(房屋建筑工程和市政公用工程）!","CreateTime":"2018-09-17T19:46:46.673"},{"Id":15,"Title":"上海科建工程管理有限公司科创板创立大会顺利召开","Img":"/imagestore/2018/0529/d3f75b1c-cb7e-488f-95ac-8f80f5c332fe.jpg","Type":1,"Content":"历时2个月的企业经营财务状况梳理及企业内部日常行政运营工作，通过法律法规整合管理，企业各大部门如财务、运营、项目管理、技术研发，都形成了各自的工作流程，各部门相互配合，为科建今后工程管理标准化软件的广泛使用，为成为项目管理行业的佼佼者努力。2018年3月12日上午10时上海科建工程管理股份有限公司创立大会暨2018年第一次临时股东大会顺利召开。","CreateTime":"2018-07-23T16:24:11.633"}];
      this.loading = false;
  }
};
</script>
 
<style lang="scss" scoped>
/* .el-header {
  position: absolute;
} */
.swiper-slide {
  font-size: 24px;
  // text-align: center;
  // line-height: 100px;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-content: center;

  .page {
    text-align: center;
    height: 100px;
    overflow: hidden;
    h3,
    p {
      font-size: 40px;
      font-weight: 400;
      color: #fff;
    }
  }

  .slogan {
    text-align: center;
    font-size: 50px;
    color: #fff;
    padding: 30px 0;
  }
}
//经典案例
.case-item {
  width: 1100px;
  height: 500px;
  overflow: hidden;
  margin: 0 auto;
  margin-top: 30px;
  display: flex;
  flex-wrap: wrap;
  justify-content: flex-start;
  li {
    width: 330px;
    height: 250px;
    list-style: none;
    background-repeat: no-repeat;
    background-size: cover;
    background-position: center;
    background-origin: content-box;
    margin: 5px;
    position: relative;
    overflow: hidden;

    &:hover {
      .case-item-hover {
        opacity: 1;
        transition: all 0.4s ease-in-out;
      }
    }
  }
}
//经典案例hover
.case-item-hover {
  width: 100%;
  height: 100%;
  position: absolute;
  top: 0;
  left: 0;
  opacity: 0;
  overflow: hidden;
  background-color: rgba(225, 56, 52, 0.7);

  .hover-title {
    height: 50px;
    color: #fff;
    font-size: 18px;
    overflow: hidden;
    text-overflow: ellipsis;
    white-space: nowrap;
    font-weight: 400;
    margin-top: 20px;
  }
  .bottom {
    border-bottom: 1px solid #fff;
    width: 60px;
    margin: 0 auto;
  }
  .more {
    width: 90px;
    padding: 5px 5px;
    margin: 0 auto;
    margin-top: 100px;
    border: 2px solid #fff;
    span {
      color: #fff;
      font-size: 20px;
    }
  }
}
// .swiper-slide:nth-child(2n) {
//   background: skyblue;
// }
// .swiper-slide:nth-child(2n-1) {
//   background: seashell;
// }
.slide-one {
  background: url(../assets/img/home_top.jpg) no-repeat center;
  background-size: cover;
}
.slide-two {
  background: url(../assets/img/home_do.jpg) no-repeat center;
  background-size: cover;
}
.slide-three {
  background: url(../assets/img/home_anli.jpg) no-repeat center;
  background-size: cover;
}
//最新资讯
.news-content {
  width: 1240px;
  margin: 0 auto;
  margin-top: 40px;
  display: flex;
  justify-content: center;

  &-item {
    width: 400px;
    display: flex;
    flex-direction: column;

    .item-img {
      width: 360px;
      height: 230px;
      background-repeat: no-repeat;
      background-size: cover;
      background-position: center;
      background-origin: content-box;
      margin: 0 auto;
    }
    .el-divider {
      background-color: #fff;
      height: 3px;
      .el-divider__text {
        width: 20px;
        height: 20px;
        border-radius: 50%;
        padding: 0px;
        color: #fff;
      }
    }
    .item-content {
      width: 360px;
      height: 230px;
      margin: 0 auto;
      //border: 1px solid paleturquoise;
      h3 {
        font-size: 22px;
        height: 30px;
        overflow: hidden;
        text-overflow: ellipsis;
        white-space: nowrap;
      }
      p {
        font-size: 15px;
        height: 80px;
        overflow: hidden;
        margin: 10px 0;
        text-overflow: ellipsis;
        display: -webkit-box;
        -webkit-line-clamp: 4;
        -webkit-box-orient: vertical;
        white-space: normal !important;
        word-wrap: break-word;
      }
      span {
        display: block;
        font-size: 14px;
        text-align: end;
      }
      h3,
      p,
      span {
        color: #fff;
      }
    }
  }
}
.order {
  order: -1;
}
.order-img {
  order: 1;
}
</style>