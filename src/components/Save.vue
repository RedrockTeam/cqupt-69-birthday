<template>
  <div class="save">
    <img :src="resultImg" alt class="save-img" />
    <div class="button">长按上方图片保存</div>
    <div
      class="headimg-origin"
      :style="{backgroundImage: `url(${headimg})`, display: isDisplay ? 'block' : 'none'}"
    >
      <img :src="selectedImg" alt />
    </div>
  </div>
</template>

<script>
export default {
  props: {
    resultImg: {
      type: String,
      default: ""
    },
    selectedImg: {
      type: String,
      default: ""
    },
    headimg: {
      type: String,
      default: ""
    },
    isDisplay: {
      type: Boolean,
      default: false
    }
  }
};
</script>

<style lang="scss" scoped>
.save {
  width: 100vw;
  height: 100vh;
  background-color: #f7ebb3;
  display: flex;
  flex-direction: column;
  align-items: center;
  position: relative;
  .headimg-origin {
    width: 271px;
    height: 271px;
    border-radius: 5.6vw;
    background-size: 100%;
    position: absolute;
    top: 0;
    left: 0;
    img {
      width: 271px;
      height: 271px;
      position: absolute;
      top: 0;
      left: 0;
      border-radius: 5.6vw;
    }
  }
  .save-img {
    width: 36.13vw;
    height: 36.13vw;
    border-radius: 5.6vw;
    margin-top: 9.3vw;
    margin-bottom: 68vw;
  }
  .button {
    width: 69.6vw;
    height: 14.27vw;
    border-radius: 4vw;
    background-color: #ff6c6c;
    line-height: 14.27vw;
    color: white;
    font-size: 4.8vw;
    position: absolute;
    bottom: 33.07vw;
  }
}
</style>
