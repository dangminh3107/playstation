<template>
<!-- eslint-disable vuejs-accessibility/click-events-have-key-events -->
  <div class="carousel">
    <VueSlickCarousel v-bind="settings">
      <div
        :class="['carousel-box', isActive === index ? 'active' : '']"
        v-for="(item, index) in imgCarousel"
        :key="index"
        @click="handleClick(index)"
      >
        <img :src="require(`@/assets/images/carousel/${item}`)" alt="" />
      </div>
    </VueSlickCarousel>
  </div>
</template>

<script>
export default {
  name: 'CarouselGameComponent',
  data() {
    return {
      imgCarousel: ['img_1.jpg', 'img_2.jpg', 'img_3.jpg', 'img_4.jpg', 'img_5.jpg'],
      isActive: 0,
      settings: {
        dots: false,
        focusOnSelect: true,
        infinite: true,
        speed: 500,
        slidesToShow: 5,
        slidesToScroll: 1,
        touchMove: false,
        initialSlide: this.isActive,
        responsive: [
          {
            breakpoint: 1024,
            settings: {
              slidesToShow: 3,
              slidesToScroll: 1,
              infinite: true,
              initialSlide: this.isActive,
              dots: false,
              touchMove: true,
            },
          },
          {
            breakpoint: 760,
            settings: {
              centerMode: true,
              slidesToShow: 2,
              slidesToScroll: 2,
              initialSlide: this.isActive,
              touchMove: true,
            },
          },
          {
            breakpoint: 600,
            settings: {
              centerMode: true,
              slidesToShow: 2,
              slidesToScroll: 1,
              initialSlide: this.isActive,
              touchMove: true,
            },
          },
          {
            breakpoint: 500,
            settings: {
              centerMode: true,
              slidesToShow: 1,
              slidesToScroll: 1,
              initialSlide: this.isActive,
              touchMove: true,
            },
          },
        ],
      },
    };
  },
  methods: {
    handleClick(index) {
      this.isActive = index;
      this.$emit('indexWasClicked', this.isActive);
    },
  },
};
</script>

<style lang="scss" scoped>
.carousel {
  padding: 35px 0;
  justify-content: center;
  max-width: 1320px;
  margin: 0 auto;
  overflow: hidden;
  .carousel-box {
    cursor: pointer;
    margin: 0 10px;
    border-radius: 10px;
    height: 135px;
    transition: all 0.2s ease;
    max-width: 91%;
    background: var(--black-color);
    margin: 10px;
    height: 100%;
    &.active {
      outline: 2px solid var(--main-color) !important;
      outline-offset: 4px;
    }
    &:hover {
      transform: translateY(-5px);
      box-shadow: 0 5px 8px var(--grey);
    }
    img {
      border-radius: 10px;
      width: 100%;
      height: 100%;
      object-fit: contain;
    }
  }
}
</style>
