<template>
  <div class="banner-game-v2">
    <div class="img-bg">
      <img :src="require(`@/assets/images/${objData.background}`)" alt="" />
      <div class="overlay">
        <img v-if="!!objData.overlay" :src="require(`@/assets/images/${objData.overlay}`)" alt="" />
      </div>
    </div>
    <div class="content active" ref="contentRef">
      <div class="img-content">
        <img :src="require(`@/assets/images/${objData.textImg}`)" alt="" />
      </div>
      <div class="overview" :style="{ color: objData.color }">
        <h1 v-if="!!objData.headTitle">{{ objData.headTitle }}</h1>
        <p>{{ objData.overview }}</p>
      </div>
      <div class="button">
        <button
          :style="{
            backgroundColor: objData.colorBtn,
            color: objData.colorTextBtn,
            '--button-c1': objData.colorBtn,
          }"
        >
          {{ objData.button }}
        </button>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'BannerGameV2Component',
  props: {
    objData: {
      type: Object,
      require: true,
    },
    sizeWindow: {
      type: Number,
      require: false,
    },
  },
  data() {
    return {
      isClicked: 0,
    };
  },
  created() {},
  mounted() {
    if (window.innerWidth <= 760) {
      this.$refs.contentRef.style.backgroundColor = this.objData.colorBgMobile;
    } else {
      this.$refs.contentRef.style.backgroundColor = 'unset';
    }
  },
  watch: {
    sizeWindow(size) {
      if (size <= 760) {
        this.$refs.contentRef.style.backgroundColor = this.objData.colorBgMobile;
      } else {
        this.$refs.contentRef.style.backgroundColor = 'unset';
      }
    },
  },
};
</script>

<style lang="scss" scoped>
.banner-game-v2 {
  height: fit-content;
  width: 100%;
  position: relative;
  max-height: 640px;
  overflow: hidden;
  .img-bg {
    position: relative;
    width: 100%;
    img {
      width: 100%;
      object-fit: contain;
    }
    .overlay {
      position: absolute;
      right: 38px;
      top: 0;
      height: 100%;
      object-fit: contain;
      img {
        height: 100%;
        object-fit: contain;
      }
      @media screen and (max-width: 768px) {
        right: 0;
        width: 100%;
        img {
          width: 100%;
        }
      }
    }
  }
  .content {
    position: absolute;
    left: 8%;
    top: 25%;
    max-width: 42%;
    &.active {
      animation: fadeUpContent 1.2s linear forwards;
    }
    @media screen and (max-width: 768px) {
      max-width: 100%;
      display: flex;
      flex-direction: column;
      left: 0;
      padding: 0 20px;
      justify-content: center;
      align-items: center;
      position: unset;
      padding: 30px 20px;
    }
    .img-content {
      img {
        max-width: 400px;
        object-fit: contain;
      }
      @media screen and (max-width: 1100px) and (min-width: 767px) {
        max-width: 100%;
      }
    }
    .overview {
      margin: 30px 0 40px;
      font-size: 1.7rem;
      @media screen and (max-width: 1100px) and (min-width: 767px) {
        font-size: 1.5vw;
        margin: 5% 0 5%;
      }
    }
    .button {
      button {
        font-size: 1.6rem;
        font-weight: bold;
        color: var(--main-color);
        border: none;
        background: var(--button-c2);
        padding: 5px 15px 8px;
        border-radius: 20px;
        &:hover {
          outline: 3.5px solid var(--button-c1);
          outline-offset: 3px;
        }
      }
    }
  }
}
</style>
