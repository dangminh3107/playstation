<template>
  <div
    class="hits-banner"
    :style="{
      '--bg-hits': !!data.image ? 'unset' : 'linear-gradient(to bottom, #f5f5f5 0%, #f5f5f500 50%)',
    }"
  >
    <div class="img-background">
      <img v-if="!isShow" :src="require(`@/assets/images/ps4view/${data.background}`)" alt="" />
      <img v-else :src="require(`@/assets/images/ps4view/${data.backgroundMobile}`)" alt="" />
    </div>
    <div class="grid-content">
      <div
        class="content"
        :style="{
          'justify-content': data.image ? 'space-aroud' : 'space-between',
        }"
      >
        <div class="content-text">
          <h1 :style="{ color: data.colorTitle }">{{ data.title }}</h1>
          <p :style="{ color: data.colorOverview }">{{ data.overview }}</p>
        </div>
        <div class="img-content" v-if="!!data.image">
          <img :src="require(`@/assets/images/ps4view/${data.image}`)" alt="" />
        </div>
        <button
          :style="{
            color: data.colorTextBtn,
            background: data.colorBtn,
            '--color': data.colorBtn,
          }"
        >
          {{ data.contentBtn }}
        </button>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'BannerHitComponent',
  props: {
    dataArr: {
      type: Object,
      require: true,
    },
    sizeWidth: {
      type: Number,
      require: true,
    },
  },
  data() {
    return {
      data: this.dataArr,
      isShow: false,
    };
  },
  mounted() {
    if (window.innerWidth < 768) this.isShow = true;
    else {
      this.isShow = false;
    }
  },
  watch: {
    sizeWidth() {
      console.log(this.isShow);
      if (window.innerWidth < 768) this.isShow = true;
      else {
        this.isShow = false;
      }
    },
  },
};
</script>

<style lang="scss" scoped>
.hits-banner {
  position: relative;
  display: flex;
  align-items: center;
  max-height: 650px;
  justify-self: center;
  overflow: hidden;
  min-height: 560px;
  @media screen and (max-width: 500px) {
    height: 480px;
  }
  &:after {
    content: "";
    position: absolute;
    top: 0;
    right: 0;
    bottom: 0;
    left: 0;
    width: 100%;
    height: 100%;
    background: var(--bg-hits);
  }
  .img-background {
    height: 100%;
    width: 100%;
    img {
      width: 100%;
      min-height: 560px;
    }
  }
  .grid-content {
    position: absolute;
    width: 100%;
    display: flex;
    height: 100%;
    justify-content: center;
    z-index: 2;
    padding-bottom: 40px;
    .content {
      max-width: 1320px;
      display: flex;
      flex-direction: column;
      align-items: center;
      width: 100%;
      justify-content: space-around;
      padding: 20px;
      @media screen and (max-width: 1024px) {
        justify-content: center !important;
      }
      .content-text {
        text-align: center;
        display: flex;
        flex-direction: column;
        width: 100%;
        align-items: center;
        padding: 20px;
        h1 {
          font-size: 4rem;
          line-height: 4rem;
          font-weight: 400;
        }
        p {
          margin-top: 30px;
          max-width: 65%;
          font-size: 1.6rem;
          font-weight: 400;
          text-align: center;
          @media screen and (max-width: 680px) {
            max-width: 100%;
            font-size: 3vw;
          }
        }
      }
      .img-content {
        @media screen and (max-width: 1024px) {
          margin: 64px 0 30px;
        }
        img {
          width: 100%;
          object-fit: contain;
        }
      }
      button {
        border: none;
        border-radius: 20px;
        padding: 6px 10px 8px;
        font-size: 1.6rem;
        font-weight: bold;
        &:hover {
          outline: 3px solid var(--color);
          outline-offset: 3px;
        }
      }
    }
  }
}
</style>
