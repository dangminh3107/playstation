<template>
  <div class="b-console">
    <div class="grid-1330">
      <div class="overview">
        <h2>{{ consoleArr[currIndex].subTitle }}</h2>
        <h1>{{ consoleArr[currIndex].title }}</h1>
        <p>{{ consoleArr[currIndex].text }}</p>
        <button>{{ consoleArr[currIndex].button }}</button>
      </div>
      <div class="image active" ref="imgRef">
        <img :src="require(`@/assets/images/equipment/${consoleArr[currIndex].image}`)" alt="" />
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'BannerConsoleComponent',
  props: ['indexClicked'],
  data() {
    return {
      consoleArr: [
        {
          subTitle: '',
          title: 'PlayStation 5 Console',
          text: 'Experience an all-new generation of incredible PlayStation games',
          button: 'Learn more',
          image: 'img_13.jpg',
        },
        {
          subTitle: '',
          title: 'DualSense™ Wireless Controller',
          text: 'Immerse yourself in the gaming experience with a controller the supports responsive haptic feedback and dynamic trigger effects.',
          button: 'Learn more',
          image: 'img_14.jpg',
        },
        {
          subTitle: 'HOW GAMES WERE MADE TO SOUND™',
          title: 'PULSE 3D™ Wireless Headset',
          text: 'Enjoy a seamless wireless experience with a headset fine-tuned for 3D Audio.',
          button: 'Learn more',
          image: 'img_15.jpg',
        },
        {
          subTitle: '',
          title: 'Media remote',
          text: 'Conveniently control movies, streaming services and more on your PS5 console with an intuitive layout.',
          button: 'Learn more',
          image: 'img_16.jpg',
        },
        {
          subTitle: '',
          title: 'HD Camera',
          text: 'Add yourself to your gameplay videos and broadcasts with smooth, sharp, full-HD capture.',
          button: 'Learn more',
          image: 'img_17.jpg',
        },
        {
          subTitle: '',
          title: 'PS5 Console Covers',
          text: 'Personalise your PlayStation 5 or PlayStation 5 Digital Edition console with a vibrant array of new colour options.*',
          button: 'Find out more',
          image: 'img_18.jpg',
        },
      ],
      currIndex: this.indexClicked,
    };
  },
  watch: {
    indexClicked(newVal) {
      this.currIndex = newVal;
      this.$refs.imgRef.classList.remove('active');
      setTimeout(() => {
        this.$refs.imgRef.classList.add('active');
      }, 100);
    },
  },
};
</script>

<style lang="scss" scoped>
.b-console {
  display: flex;
  justify-content: center;
  height: 800px;
  @media screen and (max-width: 760px) {
    height: fit-content;
  }
  .grid-1330 {
    position: relative;
    display: grid;
    grid-template-columns: 30% 60%;
    justify-content: space-between;
    max-width: 1330px;
    width: 100%;
    align-items: center;
    @media screen and (max-width: 760px) {
      display: flex;
      flex-direction: column-reverse;
      margin-bottom: 40px;
    }
    .overview {
      @media screen and (max-width: 760px) {
        display: flex;
        flex-direction: column;
        justify-content: center;
        align-items: center;
      }
      height: fit-content;
      h2 {
        color: var(--main-color);
      }
      h1 {
        font-size: 3rem;
      }
      p {
        font-size: 2rem;
        margin: 40px 0 20px;
        color: var(--light-text);
      }
      button {
        font-size: 2rem;
        line-height: 2rem;
        font-weight: bold;
        color: var(--white-color);
        background: var(--main-color);
        padding: 5px 15px 10px;
        border-radius: 20px;
        border: none;
        outline: 2px solid var(--main-color);
        &:hover {
          outline-offset: 4px;
        }
      }
    }
    .image {
      display: flex;
      flex-direction: column;
      justify-content: center;
      align-items: center;
      min-height: 800px;
      opacity: 0;
      &.active {
        animation: fadeOpacity 1s ease forwards;
      }
      img {
        width: 100%;
        object-fit: contain;
      }
    }
  }
}
</style>
