<template>
  <div
    class="banner"
    :style="{
      backgroundImage: isMobile
        ? 'url(' + require(`@/assets/images/${data.imageMobile}`) + ')'
        : 'url(' + require(`@/assets/images/${data.image}`) + ')',
    }"
    ref="bannerRef"
  >
    <div class="content active" ref="myRef">
      <div class="content-wrapper">
        <div class="image-contain">
          <img :src="require(`@/assets/images/${data.imageTitle}`)" alt="" />
        </div>
        <div class="text-contain" :style="{ color: `${data.color}` }">
          <h1>{{ data.title }}</h1>
          <p>{{ data.overview }}</p>
        </div>
        <div class="button">
          <button>Find out more</button>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'BannerGameComponent',
  props: ['indexClicked', 'listItem'],
  data() {
    return {
      currentIndex: this.indexClicked,
      data: this.listItem[this.indexClicked],
      isMobile: false,
    };
  },
  created() {
    window.addEventListener('resize', this.handleResize);
  },
  destroyed() {
    window.removeEventListener('resize', this.handleResize);
  },
  mounted() {
    if (window.innerWidth <= 768) {
      this.isMobile = true;
    }
  },
  watch: {
    indexClicked() {
      this.data = this.listItem[this.indexClicked];
      this.currentIndex = this.indexClicked;
      this.$refs.myRef.classList.remove('active');
      setTimeout(() => {
        this.$refs.myRef.classList.add('active');
      }, 100);
    },
  },
  methods: {
    handleResize() {
      if (window.innerWidth <= 768) this.isMobile = true;
      else this.isMobile = false;
      this.$emit('sizeOfWindow', window.innerWidth);
    },
  },
};
</script>

<style lang="scss" scoped>
.banner {
  width: 100%;
  background: var(--black-color);
  background-repeat: no-repeat;
  background-size: cover;
  background-position: center;
  min-height: 570px;
  display: flex;
  align-items: center;
  transition: all 0.5s linear;
  overflow: hidden;
  position: relative;
  @media screen and (max-width: 768px) {
    min-height: 660px;
  }
  &:before {
    content: "";
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    position: absolute;
    z-index: 20;
    background: linear-gradient(45deg, var(--black-color) 0%, transparent 50%);
  }
  .content {
    position: absolute;
    left: 7%;
    bottom: 10%;
    align-items: center;
    opacity: 0;
    z-index: 30;
    &.active {
      animation: fadeUpContent 1.2s linear forwards;
    }
    @media screen and (max-width: 768px) {
      left: 0;
      padding: 0 20px;
    }
    .content-wrapper {
      display: flex;
      justify-content: center;
      flex-direction: column;
      left: 6%;
      max-width: 500px;
      @media screen and (max-width: 768px) {
        align-items: center;
        text-align: center;
      }
      .image-contain {
        img {
          max-height: 250px;
          max-width: 500px;
          object-fit: contain;
          @media screen and (max-width: 768px) {
            max-width: 70%;
          }
        }
      }
      .text-contain {
        h1 {
          font-size: 4rem;
          line-height: 4rem;
          font-weight: normal;
          margin-top: 20px;
          @media screen and (max-width: 768px) {
            font-size: 3rem;
            line-height: 3rem;
          }
        }
        p {
          margin: 20px 0 30px;
          font-size: 1.6rem;
          line-height: 2.4rem;
          @media screen and (max-width: 768px) {
          }
        }
      }
      .button {
        button {
          border: none;
          padding: 10px 20px;
          border-radius: 20px;
          outline: none;
          color: var(--white-color);
          background: var(--main-color);
          cursor: pointer;
          font-size: 1.6rem;
          font-weight: bold;
          position: relative;
          outline: 2px solid var(--main-color);
          &:hover {
            outline-offset: 4px;
          }
        }
      }
    }
  }
}
</style>
