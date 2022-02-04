<template>
  <div class="product">
    <banner img="../assets/img/bgtop.jpg" title="产品中心" />
    <div class="product-content">
      <div v-for="item in productList" :key="item.id" class="product-item">
        <img :src="item.url" alt="">
      </div>
    </div>
  </div>
</template>

<script>
import Banner from "../components/Banner";
export default {
  data() {
    return {
      loading: false,
      videoSrc: "http://www.shkjem.com/video/kj.mp4",
      productList: [
        {
          id: 0,
          url: require('../assets/img/ps/pscp_img0.jpg')
        },
        {
          id: 1,
          url: require('../assets/img/ps/pscp_img1.jpg')
        },
        {
          id: 2,
          url: require('../assets/img/ps/pscp_img2.jpg')
        },
        {
          id: 3,
          url: require('../assets/img/ps/pscp_img3.jpg')
        },
        {
          id: 4,
          url: require('../assets/img/ps/pscp_img4.jpg')
        },
        {
          id: 5,
          url: require('../assets/img/ps/pscp_img5.jpg')
        },
        {
          id: 6,
          url: require('../assets/img/ps/pscp_img6.jpg')
        },
        {
          id: 7,
          url: require('../assets/img/ps/pscp_img7.jpg')
        },
        {
          id: 8,
          url: require('../assets/img/ps/pscp_img8.jpg')
        },
        {
          id: 9,
          url: require('../assets/img/ps/pscp_img9.jpg')
        },
        {
          id: 10,
          url: require('../assets/img/ps/pscp_img10.jpg')
        },
        {
          id: 11,
          url: require('../assets/img/ps/pscp_img11.jpg')
        },
        {
          id: 12,
          url: require('../assets/img/ps/pscp_img12.jpg')
        },
        {
          id: 13,
          url: require('../assets/img/ps/pscp_img13.jpg')
        },
        {
          id: 14,
          url: require('../assets/img/ps/pscp_img14.jpg')
        },
        {
          id: 15,
          url: require('../assets/img/ps/pscp_img15.jpg')
        },
        {
          id: 16,
          url: require('../assets/img/ps/pscp_img16.jpg')
        },
        {
          id: 17,
          url: require('../assets/img/ps/pscp_img17.jpg')
        },
        {
          id: 18,
          url: require('../assets/img/ps/pscp_img18.jpg')
        },
        {
          id: 19,
          url: require('../assets/img/ps/pscp_img19.jpg')
        },
        {
          id: 20,
          url: require('../assets/img/ps/pscp_img20.jpg')
        },
        {
          id: 21,
          url: require('../assets/img/ps/pscp_img21.jpg')
        },
        {
          id: 22,
          url: require('../assets/img/ps/pscp_img22.jpg')
        },
        {
          id: 23,
          url: require('../assets/img/ps/pscp_img23.jpg')
        },
        {
          id: 24,
          url: require('../assets/img/ps/pscp_img24.jpg')
        },
        {
          id: 25,
          url: require('../assets/img/ps/pscp_img25.jpg')
        },
        {
          id: 26,
          url: require('../assets/img/ps/pscp_img26.jpg')
        },
        {
          id: 27,
          url: require('../assets/img/ps/pscp_img27.jpg')
        },
        {
          id: 28,
          url: require('../assets/img/ps/pscp_img28.jpg')
        },
        {
          id: 29,
          url: require('../assets/img/ps/pscp_img29.jpg')
        },
        {
          id: 30,
          url: require('../assets/img/ps/pscp_img30.jpg')
        },
        {
          id: 31,
          url: require('../assets/img/ps/pscp_img31.jpg')
        },
        {
          id: 32,
          url: require('../assets/img/ps/pscp_img32.jpg')
        },
        {
          id: 33,
          url: require('../assets/img/ps/pscp_img33.jpg')
        },
        {
          id: 34,
          url: require('../assets/img/ps/pscp_img34.jpg')
        },
        {
          id: 35,
          url: require('../assets/img/ps/pscp_img35.jpg')
        },
        {
          id: 36,
          url: require('../assets/img/ps/pscp_img36.jpg')
        },
        {
          id: 37,
          url: require('../assets/img/ps/pscp_img37.jpg')
        },
        {
          id: 38,
          url: require('../assets/img/ps/pscp_img38.jpg')
        },
        {
          id: 39,
          url: require('../assets/img/ps/pscp_img39.jpg')
        },
        {
          id: 40,
          url: require('../assets/img/ps/pscp_img40.jpg')
        },
        {
          id: 41,
          url: require('../assets/img/ps/pscp_img41.jpg')
        },
        {
          id: 42,
          url: require('../assets/img/ps/pscp_img42.jpg')
        },
        {
          id: 43,
          url: require('../assets/img/ps/pscp_img43.jpg')
        },
        {
          id: 44,
          url: require('../assets/img/ps/pscp_img44.jpg')
        },
        {
          id: 45,
          url: require('../assets/img/ps/pscp_img45.jpg')
        },
        {
          id: 46,
          url: require('../assets/img/ps/pscp_img46.jpg')
        },
        {
          id: 47,
          url: require('../assets/img/ps/pscp_img47.jpg')
        },
        {
          id: 48,
          url: require('../assets/img/ps/pscp_img48.jpg')
        },
        {
          id: 49,
          url: require('../assets/img/ps/pscp_img49.jpg')
        },
        {
          id: 50,
          url: require('../assets/img/ps/pscp_img50.jpg')
        },
        {
          id: 51,
          url: require('../assets/img/ps/pscp_img51.jpg')
        },
        {
          id: 52,
          url: require('../assets/img/ps/pscp_img52.jpg')
        },
        {
          id: 53,
          url: require('../assets/img/ps/pscp_img53.jpg')
        },
        {
          id: 54,
          url: require('../assets/img/ps/pscp_img54.jpg')
        },
        {
          id: 55,
          url: require('../assets/img/ps/pscp_img55.jpg')
        },
        {
          id: 56,
          url: require('../assets/img/ps/pscp_img56.jpg')
        },
        {
          id: 57,
          url: require('../assets/img/ps/pscp_img57.jpg')
        },
        // {
        //   id: 58,
        //   url: require('../assets/img/ps/pscp_img58.jpg')
        // }

      ],
    }
    //   playerOptions: {
    //     playbackRates: [0.5, 1.0, 1.5, 2.0, 4.0, 8.0], //可选择的播放速度
    //     autoplay: false, //如果true,浏览器准备好时开始回放。
    //     muted: false, // 默认情况下将会消除任何音频。
    //     loop: false, // 视频一结束就重新开始。
    //     preload: "auto", // 建议浏览器在<video>加载元素后是否应该开始下载视频数据。auto浏览器选择最佳行为,立即开始加载视频（如果浏览器支持）
    //     language: "zh-CN",
    //     aspectRatio: "16:9", // 将播放器置于流畅模式，并在计算播放器的动态大小时使用该值。值应该代表一个比例 - 用冒号分隔的两个数字（例如"16:9"或"4:3"）
    //     fluid: true, // 当true时，Video.js player将拥有流体大小。换句话说，它将按比例缩放以适应其容器。
    //     sources: [
    //       {
    //         type: "",
    //         src: "http://www.shkjem.com/video/kj.mp4" //url地址
    //       }
    //     ],
    //     //poster: "../assets/img/home_top.jpg", //你的封面地址
    //     // width: document.documentElement.clientWidth,
    //     notSupportedMessage: "此视频暂无法播放，请稍后再试", //允许覆盖Video.js无法播放媒体源时显示的默认信息。
    //     controlBar: {
    //       timeDivider: true, //当前时间和持续时间的分隔符
    //       durationDisplay: true, //显示持续时间
    //       remainingTimeDisplay: false, //是否显示剩余时间功能
    //       fullscreenToggle: true //全屏按钮
    //     }
    //   }
    // };
  },
  components: {
    Banner
  },
  created() {
    // this.$http
    //   .get(
    //     "DataDictionary/GetDataDictionaryAll?key=%E4%BA%A7%E5%93%81%E8%A7%86%E9%A2%91%E9%93%BE%E6%8E%A5"
    //   )
    //   .then(response => {
    //     console.log(JSON.stringify(response.data[0].Content));
    //     // this.videoSrc = response.data[0].Content;
    //     // window.console.log(this.videoSrc);
    //     // this.loading = false;
    //   })
    //   .catch(function(error) {
    //     window.console.log(error);
    //   });
    this.videoSrc = "http://www.shkjem.com/video/kj.mp4"
  }
};
</script>

<style lang="scss" scoped>
.product {
  width: 100%;
  height: 100%;
  background-color: #14679f;
}

.product-content {
  display: flex;
  flex-wrap: wrap;
  justify-content: space-between;
  width: 1240px;
  margin: 0 auto;
  padding: 10px;
  background-color: #fff;
}

.product-item {
  margin-bottom: 5px;
  width: 33%;
  height: 280px;
  &:nth-child(3n) {
    margin-right: 0;
  }
  img {
    height: 100%;
    width: 100%;
  }
}
</style>