<template>
  <div id="app">
    <div class="app-box" :style="pagePositionStyle">
      <entrance
        @get-headimg="getHeadimg"
        :selectedImg="this.selected === 1 ? year : badge"
        :headimg="headimg"
        :isDisplay="isDisplay"
      ></entrance>
      <generate
        @generate-headimg="generateImg"
        :year="year"
        :badge="badge"
        :headimg="headimg"
      ></generate>
      <save
        :resultImg="resultImg"
        :selectedImg="this.selected === 1 ? year : badge"
        :headimg="headimg"
        :isDisplay="isDisplay"
      ></save>
    </div>
  </div>
</template>

<script>
import Entrance from "./components/Entrance";
import Generate from "./components/Generate";
import Save from "./components/Save";
import year from "./assets/69.png";
import badge from "./assets/badge.png";

export default {
  name: "app",
  components: {
    Entrance,
    Generate,
    Save
  },
  data() {
    return {
      pagePosition: 0,
      selected: 1,
      year,
      badge,
      headimg:
        "https://wx.redrock.team/wxlogo/mmopen/vi_32/UOP3N4KUFv639su5p7WbVTrQNOegGH8HKwMOEQbL0Dhzhzn1gaERweAvfxiaceICHBmgTPWWibhxj5icXicQRliax2Q/132",
      resultImg: "",
      isDisplay: false
    };
  },
  computed: {
    pagePositionStyle() {
      return {
        transform: `translate(0, ${this.pagePosition}vh)`
      };
    }
  },
  methods: {
    generateImg(value) {
      const { selected, resultImg } = value;
      this.selected = selected;
      this.resultImg = resultImg;
      this.isDisplay = false
      this.pagePosition -= 100;
    },
    getHeadimg() {
      this.pagePosition -= 100
      setTimeout(() => {
        this.isDisplay = true
      }, 1000)
    }
  },
  mounted() {
    try {
      const token = localStorage.getItem("token_69_birthday");
      const payload = token.split(".")[0].replace("%20", "+");
      const info = JSON.parse(atob(payload));
      let uri = info.headImgUrl.replace(
        "http://thirdwx.qlogo.cn/",
        "https://wx.redrock.team/wxlogo/"
      );
      this.headimg = uri;
    } catch (err) {
      console.log(err);
    }
  }
};
</script>

<style lang="scss">
body {
  margin: 0;
}
#app {
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  width: 100vw;
  height: 100vh;
  overflow: hidden;
  .app-box {
    width: 100vw;
    height: 300vh;
    letter-spacing: 1px;
    transition-duration: 1s;
  }
}
</style>
