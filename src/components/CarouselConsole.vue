<template>
<!-- eslint-disable vuejs-accessibility/click-events-have-key-events -->
  <div class="carousel-console">
    <div class="grid-1330">
      <VueSlickCarousel v-bind="settings" class="vue-c">
        <div
          :class="['console-item', isClicked === index ? 'add-outline' : '']"
          v-for="(item, index) in list"
          :key="index"
          @click="() => handleClick(index)"
        >
          <div class="console-img">
            <img :src="require(`@/assets/images/equipment/${item.img}`)" alt="" />
          </div>
          <div class="console-text">
            <span>{{ item.text }}</span>
          </div>
        </div>
      </VueSlickCarousel>
    </div>
  </div>
</template>

<script>
export default {
  name: 'CarouseConsoleComponent',
  data() {
    return {
      list: [
        {
          img: 'img_13.jpg',
          text: 'PS5 Console',
        },
        {
          img: 'img_14.jpg',
          text: 'DualSense™ Wireless Controller',
        },
        {
          img: 'img_15.jpg',
          text: 'Pulse 3D Wireless Headset',
        },
        {
          img: 'img_16.jpg',
          text: 'PlayStation 5 Media remote',
        },
        {
          img: 'img_17.jpg',
          text: 'HD Camera',
        },
        {
          img: 'img_18.jpg',
          text: 'PS5 Console Covers',
        },
      ],
      settings: {
        dots: false,
        infinite: true,
        speed: 500,
        slidesToShow: 6,
        slidesToScroll: 3,
        touchMove: false,
        responsive: [
          {
            breakpoint: 1024,
            settings: {
              dots: true,
              infinite: true,
              centerMode: true,
              centerPadding: '20px',
              slidesToShow: 3,
              slidesToScroll: 1,
              variableWidth: true,
              touchMove: true,
            },
          },
          {
            breakpoint: 760,
            settings: {
              dots: true,
              infinite: true,
              centerMode: true,
              centerPadding: '20px',
              slidesToShow: 1,
              slidesToScroll: 1,
              variableWidth: true,
              touchMove: true,
            },
          },
        ],
      },
      isClicked: 0,
    };
  },
  watch: {
    isClicked() {
      this.$emit('indexConsole', this.isClicked);
    },
  },
  methods: {
    handleClick(index) {
      this.isClicked = index;
    },
  },
};
</script>

<style lang="scss" scoped>
.carousel-console {
  overflow: hidden;
  padding-bottom: 40px;
  .grid-1330 {
    max-width: 1330px;
    margin: 0 auto;
    .vue-c {
      margin: 0 -10px;
      height: 184px;
      .console-item {
        width: 180px !important;
        justify-content: center;
        display: flex !important;
        flex-direction: column;
        align-items: center;
        cursor: pointer;
        min-height: 170px;
        opacity: 0.7;
        &.add-outline {
          opacity: 1;
          border-radius: 20px;
          border: 2px solid var(--main-color);
        }
        &:hover {
          opacity: 1;
        }
        .console-img {
          padding-top: 10px;
          height: 120px;
          img {
            width: 100%;
            height: 100%;
            object-fit: contain;
          }
        }
        .console-text {
          font-size: 124%;
          padding: 10px 20px;
          font-weight: bold;
        }
      }
    }
  }
}
</style>
