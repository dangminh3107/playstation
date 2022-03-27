<template>
  <!-- eslint-disable max-len -->
  <div
    class="plus-block"
    :style="{
      backgroundImage:
        'url(' +
        require(`@/assets/images/${isMobile ? data.backgroundMobile : data.background}`) +
        ')',
    }"
    ref="plusRef"
  >
    <div class="content" ref="contentRef" :style="{ background: data.colorBoxContent }">
      <div class="img-head">
        <img :src="require(`@/assets/images/${data.textImg}`)" alt="" />
      </div>
      <div class="text" :style="{ color: data.color }">
        <h1 :style="{ color: data.colorTitle }">{{ data.headTitle }}</h1>
        <p :style="{ color: data.colorOverview }">{{ data.overview }}</p>
        <button
          :style="{
            backgroundColor: data.colorBtn,
            color: data.colorTextBtn,
            '--button-c1': data.colorBtn,
          }"
        >
          {{ data.button }}
        </button>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  // eslint-disable-next-line quotes
  name: "BannerPlusComponent",
  // eslint-disable-next-line quotes
  props: ["dataArr", "sizeWidth"],
  data() {
    return {
      data: this.dataArr,
      isMobile: false,
    };
  },
  mounted() {
    // eslint-disable-next-line quotes
    this.$refs.contentRef.classList.add("active");
    if (window.innerWidth < 760) this.isMobile = true;
    else this.isMobile = false;
  },
  watch: {
    sizeWidth() {
      if (this.sizeWidth < 760) {
        this.isMobile = true;
      } else {
        this.isMobile = false;
      }
    },
  },
};
</script>

<style lang="scss" scoped>
.plus-block {
  min-height: 640px;
  background-repeat: no-repeat;
  background-size: cover;
  background-position: center;
  position: relative;
  display: flex;
  flex-direction: column;
  align-items: start;
  justify-content: space-around;
  .content {
    padding: 20px;
    display: flex;
    flex-direction: column;
    position: absolute;
    max-width: 44%;
    left: 8%;
    bottom: 20%;
    &.active {
      animation: fadeUpContent 1.2s linear forwards;
    }
    @media screen and (max-width: 1024px) {
      max-width: 50%;
    }
    @media screen and (max-width: 768px) {
      max-width: 100%;
      display: flex;
      flex-direction: column;
      left: 0;
      justify-content: center;
      align-items: center;
      position: unset;
      padding: 30px 20px;
      margin: 0 20px;
    }
    .img-head {
      img {
        max-width: 70%;
        object-fit: contain;
      }
      @media screen and (max-width: 1100px) and (min-width: 767px) {
        max-width: 100%;
      }
    }
    .text {
      h1 {
        font-size: 2.5rem;
        line-height: 2.5rem;
        margin: 20px 0;
        @media screen and (max-width: 768px) {
          font-size: 4.5vw;
          line-height: 4.5vw;
        }
      }
      p {
        margin: 20px 0 30px;
        font-size: 1.7rem;
        @media screen and (max-width: 1100px) and (min-width: 767px) {
          font-size: 1.5vw;
          margin: 5% 0 5%;
        }
      }
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
