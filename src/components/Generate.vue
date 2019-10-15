<template>
  <div class="generate">
    <div class="headimg-origin" :style="{backgroundImage: `url(${headimg})`}">
      <img :src="selectedImg" alt />
    </div>
    <div class="headimg-choose">
      <div
        class="headimg-69"
        :style="{backgroundColor: selected === 1 ? '#ffffff' : '#fff9dc'}"
        @click="select69"
      >
        <img src="../assets/69-example.png" alt />
        <p>69周年</p>
      </div>
      <div
        class="headimg-badge"
        :style="{backgroundColor: selected === 2 ? '#ffffff' : '#fff9dc'}"
        @click="selectBadge"
      >
        <img src="../assets/badge-example.png" alt />
        <p>校徽纪念</p>
      </div>
    </div>
    <p>请选择您想要的款式</p>
    <div
      class="button"
      @click="generateImg"
      :style="{backgroundColor: isGenerating ? '#fab6b6' : '#ff6c6c'}"
    >{{isGenerating ? '生成中...' : '生成头像'}}</div>
  </div>
</template>

<script>
// import domtoimage from 'dom-to-image'
import html2canvas from "html2canvas";
export default {
  name: "generate",
  props: {
    year: {
      type: String,
      default: ""
    },
    badge: {
      type: String,
      default: ""
    },
    headimg: {
      type: String,
      default: ""
    }
  },
  data() {
    return {
      /**
       * selected为1 选中69周年版
       * selected为2 选中校徽版
       */
      selected: 1,
      isGenerating: false
    };
  },
  computed: {
    selectedImg() {
      return this.selected === 1 ? this.year : this.badge;
    }
  },
  methods: {
    select69() {
      this.selected = 1;
      this.$emit("changeSelected", 1)
    },
    selectBadge() {
      this.selected = 2;
      this.$emit("changeSelected", 2)
    },
    async generateImg() {
      if (this.isGenerating) {
        return;
      }
      this.isGenerating = true;
      const canvas = await html2canvas(document.body, {
        x: 0,
        y: 0,
        width: 271,
        height: 271
      });
      const resultImg = canvas.toDataURL();
      this.isGenerating = false;
      this.$emit("generate-headimg", {
        selected: this.selected,
        resultImg
      });
    }
  }
};
</script>

<style lang="scss" scoped>
.generate {
  width: 100vw;
  height: 100vh;
  background-color: #f7ebb3;
  box-sizing: border-box;
  padding-top: 9.3vw;
  position: relative;
  .headimg-origin {
    width: 36.13vw;
    height: 36.13vw;
    border-radius: 5.6vw;
    background-size: 100%;
    position: relative;
    margin: 0 auto;
    img {
      width: 36.13vw;
      height: 36.13vw;
      position: absolute;
      top: 0;
      left: 0;
      border-radius: 5.6vw;
    }
  }
  .headimg-choose {
    width: 100vw;
    height: 41.33vw;
    margin-top: 7.73vw;
    display: flex;
    justify-content: space-between;
    box-sizing: border-box;
    padding-left: 12.4vw;
    padding-right: 12.4vw;
    margin-bottom: 4.27vw;
    p {
      color: #383838;
      font-size: 4vw;
      margin-top: 2.5vw;
      margin-bottom: 0;
    }
    img {
      width: 26vw;
      height: 26vw;
      margin-top: 3.33vw;
    }
    .headimg-69 {
      width: 32vw;
      height: 100%;
      border-radius: 4vw;
      transition: background-color 0.2s;
    }
    .headimg-badge {
      width: 32vw;
      height: 100%;
      border-radius: 4vw;
      transition: background-color 0.2s;
    }
  }
  p {
    font-size: 3.2vw;
    color: #8b8565;
    margin-top: 0;
    margin-bottom: 10.93vw;
  }
  .button {
    width: 69.6vw;
    height: 14.27vw;
    border-radius: 4vw;
    background-color: #ff6c6c;
    line-height: 14.27vw;
    color: white;
    font-size: 4.8vw;
    transition: background-color 0.2s;
    position: absolute;
    left: 50%;
    transform: translate(-50%, 0);
  }
}
</style>
