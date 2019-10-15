<template>
  <div class="entrance">
    <img src="../assets/entrance-text.png" alt="一朝重邮人 一生重邮情" class="entrance-text" />
    <div class="button" @click="$emit('get-headimg')">获取头像</div>
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
@keyframes appear {
  0% {
    transform: translate(0, 20vh);
  }
  70% {
    transform: translate(0, -1vh);
  }
  100% {
    transform: translate(0, 0);
  }
}
.entrance {
  width: 100vw;
  height: 100vh;
  background-image: url("../assets/entrance-bg.png");
  background-size: cover;
  background-repeat: no-repeat;
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
  .entrance-text {
    width: 56.27vw;
    height: 47.33vw;
    margin-top: 22.13vw;
    animation: appear 1s;
  }
  .button {
    width: 69.6vw;
    height: 14.27vw;
    border-radius: 4vw;
    background-color: #ff6c6c;
    line-height: 14.27vw;
    color: white;
    font-size: 4.8vw;
    margin-top: 52vw;
    // position: absolute;
    // bottom: 33.07vw;
  }
}
</style>
