<template>
  <div class="banner-static-v1">
    <div class="banner">
      <div class="mask" ref="refMask"></div>
      <img :src="require(`@/assets/images/ps4view/banner_1/${banner1.image}`)" alt="" />
    </div>
    <div class="overlay" ref="refOverlay">
      <div class="overlay-logo">
        <img :src="require(`@/assets/images/ps4view/banner_1/${banner1.logo}`)" alt="" />
      </div>
      <div class="text" ref="textOverlay">
        <span v-for="(item, index) in banner1.text" :key="index">{{ item }}</span>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  // eslint-disable-next-line quotes
  name: "BannerStaticV1Component",
  // eslint-disable-next-line quotes
  props: ["dataArr"],
  data() {
    return {
      banner1: this.dataArr,
    };
  },
  mounted() {
    this.$refs.refMask.classList.add('on-display');
    this.$refs.refOverlay.classList.add('on-display');
    this.$refs.textOverlay.classList.add('on-display');
  },
};
</script>

<style lang="scss" scoped>
.banner-static-v1 {
  position: relative;
  display: flex;
  justify-content: center;
  align-items: center;
  @media screen and (max-width: 680px) {
    flex-direction: column;
  }
  .banner {
    height: fit-content;
    width: 100%;
    position: relative;
    .mask {
      content: "";
      position: absolute;
      width: 100%;
      height: 100%;
      top: 0;
      left: 0;
      right: 0;
      bottom: 0;
      background-color: var(--custom-banner-theme);
      transition: all 1s ease-in-out;
      opacity: 1;
      &.on-display {
        animation: fadeOpacityBannerV1 1s ease-in-out forwards;
      }
    }
    img {
      width: 100%;
      object-fit: contain;
    }
  }
  .overlay {
    height: 100%;
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    position: absolute;
    padding: 160px 0 40px;
    @media screen and (max-width: 680px) {
      width: 100%;
      position: unset;
      background: linear-gradient(to bottom, #064395, #0072ce);
    }
    &.on-display {
      animation: fadeUpContent 1.2s linear forwards;
    }
    .overlay-logo {
      width: 406px;
      @media screen and (max-width: 680px) {
        width: 40%;
      }
      img {
        width: 100%;
        object-fit: contain;
      }
    }
    .text {
      display: flex;
      flex-direction: column;
      justify-content: center;
      align-items: center;
      margin-top: 30px;
      opacity: 0;
      &.on-display {
        animation: fadeUpContent 1.2s 0.5s linear forwards;
      }
      span {
        padding-bottom: 10px;
        font-size: 3.5rem;
        line-height: 3.5rem;
        color: #fff;
        font-weight: 400;
        @media screen and (max-width: 680px) {
          font-size: 2.6rem;
          line-height: 2.6rem;
        }
      }
    }
  }
}
</style>
