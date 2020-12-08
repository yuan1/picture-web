<template>
  <div class="home">
    <div class="fav-list">
      <div
        v-for="(pic, index) in pictureData"
        :key="index"
        :style="{
          flexBasis: (pic.width * 240) / pic.height + 'px',
          flexGrow: (pic.width * 100) / pic.height
        }"
      >
        <i :style="{ paddingBottom: (pic.height / pic.width) * 100 + '%' }"></i>
        <img :src="pic.watermarkImage" />
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "Home",
  data() {
    return {
      pictureData: require("@/assets/data/cats.json")
    };
  },
  created() {
    console.log(this.pictureData);
  }
};
</script>

<style lang="scss" scoped>
.home {
  width: 100%;
  height: 100%;
  .fav-list {
    display: flex;
    flex-wrap: wrap;
    margin: 2px;
    text-align: left;
    // 最后一行展示形式，可注释掉查看另一种形式
    &::after {
      content: "";
      flex-grow: 999999999;
      order: 999999999;
    }
    & > div {
      margin: 2px;
      background-color: violet;
      position: relative;
      // 加载占位符
      & > i {
        display: block;
        background-color: lightblue;
        /* display: none; */
      }
      & > img {
        position: absolute;
        vertical-align: bottom;
        top: 0;
        width: 100%;
        height: 100%;
        object-fit: cover;
      }
    }
  }
}
</style>
