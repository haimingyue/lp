<template>
  <div class="go-in">
    <banner img="../assets/img/bgtop.jpg" title="走进普石" />
    <div class="section" v-loading="loading">
      <div class="section-content">
        <div class="content-summary">
          <div class="summary-left">
            <p class="title">公司简介</p>
            <p class="eTitle">ABOUT US</p>
            <p class="content">
              普石“彩普”彩色混凝土自然石在混凝土的基础上经过多种技术和程序创造出来类似大理石、花岗石、各类砖、木材等不同格调的建筑结构及色彩图案，她不仅古朴自然，具有整体性、永久性等特点，而且又克服了天然大理石石材价格昂贵、施工麻烦、地板砖和广场砖接缝容易松动、渗水和损坏，不宜重压的不足。当您对广场通道和车道等单调呆板的水泥路面而感到乏味时，不妨考虑采用普石“彩普”彩色地面，她立体感强、图案花色选择性大，使用温度范围广、耐冲击、耐腐性强、外层颜色不会变色和褪色，具有防滑功能，对环境无影响，是一种理想的地面装饰材料，适用于地面地坪、停车场、人行道、汽车道广场、中心绿地、高尔夫球场等各种地面。
本公司拥有强大的生产和施工技术，曾在中国各个沿海城市及内地施工，如：深圳，大梅沙，东部华侨城，海南，天涯海角，广州花花世界，北京，上
海，合肥万达，福建龙岩动漫城，山东青岛等地。本公司一直本着引进开发新型建筑材料的宗旨，重在美化我们周围的环境及态度，将会成为各国建筑商对地面材料的第一选择。
            </p>
          </div>
          <div class="summary-right">
            <img src="../assets/img/jianjietopmin.jpg" alt />
          </div>
        </div>
        <el-divider class="el-divider-active">
          <i class="el-icon-arrow-down el-icon-arrow-down-active"></i>
        </el-divider>
        <!-- 发展历程 -->
        <!-- <div class="content-course">
          <div class="top">
            <h3>发展历程</h3>
            <p>DEVELOPMENT</p>
            <div class="border"></div>
            <div class="timeline"></div>
          </div>
          <div class="course-time">
            <swiper :options="swiperOption" ref="mySwiper">
              <swiper-slide v-for="(item,index) in courseList" :key="index">
                <div class="time-show">
                  <div class="time-show-item" v-for="(courseOne,one) in item" :key="one">
                    <div class="item-top" :class="{'order-top' : one%2===1}"></div>
                    <el-divider>
                      <i class="el-icon-mobile-phone"></i>
                    </el-divider>
                    <div class="item-bottom" :class="{'order' : one%2===1}">
                      <div class="item-bottom-content">
                        <p>{{courseOne.Content}}</p>
                        <p>{{courseOne.Year}}</p>
                      </div>
                    </div>
                  </div>
                </div>
              </swiper-slide>
              <div class="swiper-button-prev" slot="button-prev"></div>
              <div class="swiper-button-next" slot="button-next"></div>
            </swiper>
          </div>
        </div> -->

        <div class="content-culture">
          <h3>企业文化</h3>
          <h3>CULTURE</h3>
          <p>我们只专注一件事情——工程项目管理</p>
          <span>确保工程无重大安全事故</span>
          <span>确保工程施工单位无大面积返工</span>
          <span>确保工程材料及设备无伪劣产品</span>
          <span>确保工程管理留下痕迹、实施过程可追溯</span>
        </div>
        <!-- 公司荣誉 -->
        <div class="content-honor">
          <div class="honor-big-img">
            <el-dialog :title="dialogTitle" :visible.sync="dialogTableVisible">
              <img v-lazy="dialogUrl" alt />
            </el-dialog>
          </div>
          <div class="top">
            <h3>公司荣誉</h3>
            <p>HONOR</p>
            <div class="border"></div>
          </div>
          <ul class="honor-show">
            <li v-for="(honor,index) in honorList" :key="index">
              <img
                v-lazy="imgserver+honor.Img"
                @click="dialogTableVisible = true ;dialogUrl = imgserver + honor.Img;dialogTitle= honor.Remark"
              />
            </li>
          </ul>
          <p>点击图片查看大图</p>
        </div>
        <!-- 团队风采 -->
        <div class="content-team">
          <div class="top">
            <h3>团队风采</h3>
            <p>TEAM</p>
          </div>
          <el-carousel :interval="4000" type="card">
            <el-carousel-item v-for="(team,index) in teamItem" :key="index">
              <div class="swiper-img" v-lazy:background-image="imgserver + team.Img"></div>
            </el-carousel-item>
          </el-carousel>
        </div>
        <!-- 合作伙伴 -->
        <div class="content-partner">
          <div class="top">
            <h3>合作伙伴</h3>
            <p>RARTNERS</p>
            <ul class="partner-img">
              <li v-for="(partner,i) in partnerImg" :key="i">
                <img v-lazy="imgserver+partner.Img" alt />
              </li>
            </ul>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import Banner from "../components/Banner";
import { swiper, swiperSlide } from "vue-awesome-swiper";
export default {
  components: {
    Banner,
    swiper,
    swiperSlide
  },
  data() {
    return {
      loading: false,
      honorList: [],
      partnerImg: [],
      courseList: [],
      teamItem: [],
      swiperOption: {
        navigation: {
          nextEl: ".swiper-button-next",
          prevEl: ".swiper-button-prev"
        }
      },
      dialogTableVisible: false,
      dialogUrl: "",
      dialogTitle: ""
    };
  },
  mounted() {
    let responseHonor = [{"Id":31,"Img":"/imagestore/2018/0805/25d84da6-deaf-4503-aef2-7355ecb157ee.jpg","Remark":"高新技术企业证书","CreateTime":"2021-03-26T13:25:19.433"},{"Id":36,"Img":"/imagestore/2020/0605/16024bde-6f13-4c48-afae-76b73f485cae.jpg","Remark":"高新成果转化证书","CreateTime":"2020-06-05T21:22:10.94"},{"Id":28,"Img":"/imagestore/2019/0718/2603939b-833f-426a-9352-1f08fccec51c.jpg","Remark":"建筑工程监理服务系统V1.0 软著证书","CreateTime":"2019-07-18T16:39:18.197"},{"Id":27,"Img":"/imagestore/2019/0718/dd60cc71-3bfe-4a59-a7bf-03375358dd2a.jpg","Remark":"建筑建理工作任务发布系统V1.0 软著证书","CreateTime":"2019-07-18T16:37:20.32"},{"Id":26,"Img":"/imagestore/2018/0516/3e58a57c-0921-4284-bb70-888ea3dc3f0a.png","Remark":" 工程预算处理软件V1.0 软著证书","CreateTime":"2018-07-06T11:27:15.56"}]
    let responseEnterprise = []
    let responseTeam = [{"Id":16,"Img":"/imagestore/2019/0425/ad5bffa4-e608-4f0c-8cbd-f9daa2af8ef2.jpg","Remark":"参加第七届中国（上海）国际技术进出口交易会","CreateTime":"2020-06-05T21:34:46.743"},{"Id":11,"Img":"/imagestore/2019/0425/9db92c6e-95e9-43df-b6d4-8b2e83f85dbe.jpg","Remark":"参加第七届中国（上海）国际技术进出口交易会","CreateTime":"2020-06-05T21:34:41.023"},{"Id":6,"Img":"/imagestore/2019/0425/3ee5db59-d021-4d0d-927e-70e850303f16.jpg","Remark":"参加第七届中国（上海）国际技术进出口交易会","CreateTime":"2020-06-05T21:34:36.397"},{"Id":22,"Img":"/imagestore/2019/0426/cafb7b6a-71dd-4a9b-881b-d3f9da6b8967.jpg","Remark":"","CreateTime":"2019-04-26T16:06:18.193"},{"Id":21,"Img":"/imagestore/2019/0426/958585c0-18a3-450b-b7e1-c8ee4c2f7bec.jpg","Remark":"","CreateTime":"2019-04-26T16:06:11.277"},{"Id":20,"Img":"/imagestore/2019/0426/37af22f2-d6d8-4b10-8377-9a28fa8dd8db.jpg","Remark":"","CreateTime":"2019-04-26T16:06:03.21"},{"Id":19,"Img":"/imagestore/2019/0426/f40c7512-4057-4b2f-84dc-d8ee93d6f5e1.jpg","Remark":"","CreateTime":"2019-04-26T16:05:55.947"},{"Id":18,"Img":"/imagestore/2019/0426/f929d681-38c3-4d4f-b845-fa695f4801e8.jpg","Remark":"","CreateTime":"2019-04-26T16:05:47.69"},{"Id":17,"Img":"/imagestore/2019/0426/12633c2f-387c-4587-a88a-43666265f886.jpg","Remark":"","CreateTime":"2019-04-26T16:05:38.187"}]
    let responseCourse = [{"Id":10,"Year":"2012年9月","Content":"上海科建工程管理有限公司成立"},{"Id":11,"Year":"2016年11月","Content":"上海科建工程管理股份有限公司“工程管理标准化+互联网协作平台“开发上线，并成功投入项目使用。"},{"Id":12,"Year":"2017年11月","Content":"上海科建工程管理股份有限公司获得高新技术企业证书"},{"Id":14,"Year":"2018年3月","Content":"上海科建工程管理股份有限公司股份改制成功。"},{"Id":17,"Year":"2018年9月","Content":"上海科建工程管理股份有限公司登录上海股权托管交易中心科创板"},{"Id":18,"Year":"2019年5月","Content":"参加“创业在上海”国际创新创业大赛并获得立项"},{"Id":20,"Year":"2020年11月","Content":"公司成功通过国家高新技术企业重新认定。"},{"Id":19,"Year":"2020年3月","Content":"公司研发的 “工程管理标准化信息协作平台软件”被认定为上海市高新技术成果转化项目"}]
    this.honorList = responseHonor;
    this.partnerImg = responseEnterprise;
    this.teamItem = responseTeam;

    var groupCount = Math.ceil(responseCourse.length / 2);
    window.console.log(groupCount);
    for (let i = 0; i < groupCount; i++) {
      let img2 = [];
      for (let j = 0; j < 2; j++) {
        if (responseCourse.length - 1 >= i * 2 + j) {
          img2.push(responseCourse[i * 2 + j]);
        }
      }
      this.courseList.push(img2);
    }
    // this.$http
    //   .all([
    //     this.$http.get("Honor/GetHonorAll"),
    //     this.$http.get("Enterprise/GetEnterpriseAll"),
    //     this.$http.get(`Team/GetTeamAll`),
    //     this.$http.get(`Course/GetCourseAll`)
    //   ])
    //   .then(
    //     this.$http.spread(
    //       (responseHonor, responseEnterprise, responseTeam, responseCourse) => {
    //         console.log('responseHonor', JSON.stringify(responseHonor.data))
    //         console.log('responseEnterprise', JSON.stringify(responseEnterprise.data))
    //         console.log('responseTeam', JSON.stringify(responseTeam.data))
    //         console.log('responseCourse', JSON.stringify(responseCourse.data))
    //         this.honorList = responseHonor.data;
    //         this.partnerImg = responseEnterprise.data;
    //         this.teamItem = responseTeam.data;

    //         var groupCount = Math.ceil(responseCourse.data.length / 2);
    //         window.console.log(groupCount);
    //         for (let i = 0; i < groupCount; i++) {
    //           let img2 = [];
    //           for (let j = 0; j < 2; j++) {
    //             if (responseCourse.data.length - 1 >= i * 2 + j) {
    //               img2.push(responseCourse.data[i * 2 + j]);
    //             }
    //           }
    //           this.courseList.push(img2);
    //         }
    //         window.console.log(this.courseList);
    //         this.loading = false;
    //       }
    //     )
    //   );
  }
};
</script>

<style lang="scss" scoped>
* {
  margin: 0;
  padding: 0;
}

.go-in {
  width: 100%;
  height: 100%;
  background-color: #14679f;
  position: relative;
  overflow: hidden;
  .section {
    width: 100%;
    &-content {
      width: 1240px;
      margin: 0 auto;
      background-color: #fff;

      .content-summary {
        //height: 500px;
        display: flex;
        justify-content: space-around;
        padding: 100px 0;
        .summary-left {
          width: 600px;
          .title {
            font-size: 25px;
            color: #e13834;
          }
          .eTitle {
            font-size: 17px;
            color: #e13834;
            padding: 20px 0;
          }
          .content {
            color: #14679f;
            font-size: 14px;
            text-indent: 25px;
            line-height: 30px;
          }
        }

        .summary-right {
          width: 400px;
          height: 310px;
          border: 2px solid #1d42b9;
          //animation: imgboxkey 4s infinite;
          border-radius: 10px;
          margin-top: 80px;
          text-align: center;

          img {
            width: 360px;
            height: 270px;
            margin-top: 20px;
            //animation: imgbo 4s infinite;
          }
        }
      }

      //发展历程
      .content-course {
        padding: 50px 0;
        .course-time {
          width: 1000px;
          height: 400px;
          margin: 20px auto;
          .swiper-container {
            height: 100%;
          }
          .time-show {
            width: 700px;
            height: 100%;
            margin: 0 auto;
            display: flex;
            .time-show-item {
              width: 350px;
              height: 100%;
              overflow: hidden;
              display: flex;
              flex-direction: column;

              .item-top,
              .item-bottom {
                height: 190px;
              }
              .item-bottom {
                // display: flex;
                // align-content: center;
                .item-bottom-content {
                  background-color: #1667a0;
                  margin: 20px 0;
                  p {
                    color: #fff;
                    text-align: center;
                    padding: 15px;
                  }
                }
              }
            }
          }
        }
      }

      //企业文化
      .content-culture {
        height: 450px;
        display: flex;
        flex-direction: column;
        justify-content: center;
        align-items: flex-start;
        padding-left: 100px;
        background-color: #c2daeb;
        h3 {
          color: #3c6088;
          font-size: 26px;
        }
        p {
          color: #3c6088;
          font-size: 26px;
          padding: 5px 0;
        }
        span {
          font-weight: 400;
          line-height: 36px;
          font-size: 18px;
          padding: 5px 0;
        }
      }

      //公司荣誉
      .content-honor {
        padding: 50px 0;
        .honor-show {
          width: 1000px;
          margin: 30px auto;
          display: flex;
          flex-wrap: wrap;
          justify-content: flex-start;
          align-content: flex-start;

          li {
            width: 220px;
            height: 320px;
            margin-left: 15px;
            list-style: none;
            border: 1px solid palegoldenrod;

            img {
              width: 100%;
              height: 100%;
            }
          }
        }
        p {
          text-align: center;
          color: #3c6088;
        }
      }

      //团队风采
      .content-team {
        padding: 50px 100px;
        .swiper-img {
          height: 400px;
          background: no-repeat center;
          background-size: cover;
        }
      }

      //合作伙伴
      .content-partner {
        padding: 50px 0;
        .partner-img {
          width: 950px;
          margin: 20px auto;
          display: flex;
          justify-content: flex-start;
          flex-wrap: wrap;
          li {
            width: 107px;
            height: 107px;
            list-style: none;
            margin: 10px 25px;

            img {
              width: 100%;
              height: 100%;
              border: 1px solid rgb(194, 218, 235);
            }
          }
        }
      }
    }
  }
}

@keyframes imgboxkey {
  0% {
    border: solid rgb(29, 66, 185) 2px;
  }
  40% {
    border: solid rgb(255, 255, 255) 2px;
  }
  60% {
    border: solid rgb(255, 255, 255) 2px;
  }
  100% {
    border: solid rgb(29, 66, 185) 2px;
  }
}

@keyframes imgbo {
  0% {
    transform: scale(1);
    box-shadow: 0px 0px 0px 0px #ababab;
  }
  50% {
    transform: scale(1.1);
    box-shadow: 0px 0px 10px 5px #ababab;
  }
  100% {
    transform: scale(1);
    box-shadow: 0px 0px 0px 0px #ababab;
  }
}
.el-divider--horizontal {
  margin: 1px 0;
}

.top {
  h3,
  p {
    text-align: center;
    color: #3c6088;
    font-weight: 400;
    padding: 10px 0;
  }
  h3 {
    font-size: 30px;
  }
  p {
    font-size: 20px;
  }
  .border {
    border-bottom: 1px solid #3c6088;
    width: 15%;
    margin: 0 auto;
  }
}
// .swiper-button-disabled {
//   display: none;
// }
.order {
  order: -1;
}
.order-top {
  order: 1;
}
.el-divider {
  background-color: red;
  height: 3px;
  .el-divider__text {
    width: 20px;
    height: 20px;
    border-radius: 50%;
    padding: 0px;
    color: #fff;
    border: 3px solid red;
  }
}
.el-divider-active {
  background-color: #3c6088;
}
.honor-big-img {
  width: 100%;
  height: 100%;
  z-index: 10;
  text-align: center;
  padding-bottom: 20px;
  padding: 5%;
  //background-color: #14679f;
  .el-dialog__wrapper {
    position: fixed;
    top: 0;
    right: 0;
    bottom: 0;
    left: 0;
    overflow: auto;
    margin: 0;

    .el-dialog__body {
      overflow: hidden;
      img {
        width: 100%;
      }
    }
  }
}
</style>