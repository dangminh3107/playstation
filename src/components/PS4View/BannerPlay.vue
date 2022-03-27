<template>
  <div class="play-banner" :style="{ '--color-bg': data.colorBg }">
    <div class="img-background">
      <img :src="require(`@/assets/images/ps4view/${data.background}`)" alt="" />
    </div>
    <div class="content">
      <h1>{{ data.header }}</h1>
      <p>{{ data.overview }}</p>
      <button
        :style="{
          color: data.colorBtn,
          background: data.bgBtn,
          '--color': data.colorHover,
        }"
      >
        {{ data.btnContent }}
      </button>
    </div>
  </div>
</template>

<script>
export default {
  name: 'BannerPlayComponent',
  props: ['dataArr'],
  data() {
    return {
      data: this.dataArr,
    };
  },
};
</script>

<style lang="scss" scoped>
.play-banner {
  height: fit-content;
  position: relative;
  display: flex;
  justify-content: center;
  overflow: hidden;
  background: var(--color-bg);
  &:before {
    content: "";
    position: absolute;
    top: 0;
    left: 0;
    right: 0;
    bottom: 0;
    width: 100%;
    background: linear-gradient(to top, var(--light-text) 0%, #1f1f1f00 100%);
    z-index: 10;
  }
  @media screen and (max-width: 1024px) {
    align-items: center;
  }
  @media screen and (max-width: 600px) {
    flex-direction: column;
  }
  .img-background {
    img {
      width: 150%;
      object-position: center;
      transform: translateX(-25vw);
    }
  }
  .content {
    position: absolute;
    display: flex;
    flex-direction: column;
    align-items: center;
    bottom: 25%;
    color: var(--white-color);
    max-width: 70%;
    text-align: center;
    background: rgba(36, 23, 23, 0.5);
    padding: 20px;
    z-index: 12;
    @media screen and (max-width: 1024px) {
      bottom: unset;
    }
    @media screen and (max-width: 600px) {
      position: unset;
      margin: 30px 20px;
      max-width: unset;
    }
    h1 {
      font-size: 4rem;
      line-height: 4rem;
      font-weight: 400;
      @media screen and (max-width: 1024px) {
        font-size: 5vw;
        line-height: 5vw;
      }
      @media screen and (max-width: 600px) {
        font-size: 7vw;
      }
    }
    p {
      margin: 30px 0;
      font-size: 2rem;
      font-weight: 400;
      @media screen and (max-width: 1024px) {
        font-size: 2.2vw;
      }
      @media screen and (max-width: 600px) {
        font-size: 3vw;
      }
    }
    button {
      font-size: 1.6rem;
      font-weight: bold;
      border: none;
      border-radius: 20px;
      padding: 6px 20px 8px;
      @media screen and (max-width: 1024px) {
        font-size: 2.5vw;
      }
      @media screen and (max-width: 600px) {
      }
      &:hover {
        outline: 3px solid var(--color);
        outline-offset: 3px;
      }
    }
  }
}
</style>
