<template>
  <div class="case">
    <banner img="../assets/img/bgtop.jpg" title="精典案例" />
    <div class="case-section" v-loading="loading">
      <div class="case-section-content">
        <div class="case-section-content-list" v-for="(cas,index) in caseList" :key="index">
          <img v-lazy="imgserver+cas.Img" />
          <div class="content-list-abstract" :class="{'abstract-active' : index%2!=1}">
            <p class="abstract-title">{{cas.Title}}</p>
            <p class="abstract-content">{{cas.Content}}</p>
            <div class="more">
              <router-link
                class="text-decoration"
                :to="{ name: 'casedetails', params: { id: cas.Id }}"
              >
                <span>more</span>
                <img src="../assets/img/sanjiao.png" />
              </router-link>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>
<script>
import Banner from "../components/Banner";
export default {
  components: {
    Banner
  },
  data() {
    return {
      loading: false,
      caseList: []
    };
  },
  mounted() {
    window.console.log("case");
    // this.$http
    //   .get("Cases/GetCasesAll")
    //   .then(response => {
    //     console.log(JSON.stringify(response.data));
    //     this.caseList = response.data;
    //     //window.console.log(this.caseList);
    //     this.loading = false;
    //   })
    //   .catch(function(error) {
    //     window.console.log(error);
    //   });
    this.caseList = [{"Id":29,"Img":"/imagestore/2020/0605/439332ec-11c0-440c-8800-d94b0479c22c.jpg","Title":"上海市公共安全教育实训基地项目位","Content":"位于上海市青浦区沪青平公路6888号“东方绿舟”东南 角，四界范围为：东临城市河道，南至沪青平公路，西界绿湖路，北靠现有的东方绿舟停机 坪。项目用地面积65048平方米（以实测为准），新建总建筑面积约为26467平方米（地上 23500平方米，地下2967平方米）","Del":null,"CreateTime":"2020-06-05T21:12:45.387"},{"Id":28,"Img":"/imagestore/2020/0605/fcebfcd1-7b8c-4214-9fc4-c9c275ccaaf0.jpg","Title":"高端装备用特种电缆检测评估服务基地","Content":"高端装备用特种电缆检测评估服务基地建设 一期工程位于上海市宝山区山连路558号， 项目建筑面积为19324.03平方米（地上建 筑面积为15446.74平方米，地下建筑面积\n为3877.29平方米）。","Del":null,"CreateTime":"2020-06-05T21:05:45.157"},{"Id":27,"Img":"/imagestore/2020/0605/e6cad4d5-0f76-4241-a112-8660acf8c281.jpg","Title":"中国移动上海公司临港数据中心","Content":"上海移动临港IDC研发与产业化基地项目一 期数据中心2#机楼微模块机房配套工程","Del":null,"CreateTime":"2020-06-05T21:02:05.567"},{"Id":26,"Img":"/imagestore/2020/0605/0c6fa4a8-94da-4fc5-bac4-76c59d52c2b2.jpg","Title":"上海合作组织国际司法交流培训基地项目","Content":"上海合作组织国际司法交流合作培训基地（上海政法学院）工程位于松江区泗陈公路5488号\n上海政法学院东南部，项目用地面积66125平方米（以实测为准），新建总建筑面积约为 24976平方米，其中地上建筑面积为22476平方米，地下建筑面积约为2500平方米。","Del":null,"CreateTime":"2020-06-05T20:58:05.57"}]
  }
};
</script>

 <style lang="scss" scoped>
.case {
  width: 100%;
  height: 100%;
  position: relative;
  overflow: hidden;
  background-color: #14679f;

  &-section {
    width: 100%;
    &-content {
      width: 1240px;
      min-height: 1000px;
      margin: 0 auto;
      background-color: #fff;

      &-list {
        width: 100%;
        height: 500px;
        display: flex;
        justify-content: center;
        align-items: center;
        border: 1px solid pink;

        img {
          width: 612px;
          height: 314px;
        }
        .content-list-abstract {
          width: 290px;
          height: 350px;
          padding: 0 20px;
          display: flex;
          flex-direction: column;
          justify-content: space-around;
          .abstract-title {
            line-height: 30px;
            font-size: 22px;
            color: #e13834;
          }
          .abstract-content {
            height: 150px;
            color: #484848;
            font-size: 15px;

            overflow: hidden;
            text-overflow: ellipsis;
            display: -webkit-box;
            -webkit-line-clamp: 7;
            -webkit-box-orient: vertical;
            white-space: normal !important;
            word-wrap: break-word;
            //border: 1px solid pink;
          }
          .more {
            display: flex;
            justify-content: flex-start;
            .text-decoration {
              text-decoration: none;

              span {
                color: #000;
              }
              img {
                width: 12px;
                height: 12px;
              }
            }
          }
        }
        .abstract-active {
          order: -1;
        }
      }
    }
  }
}
</style>