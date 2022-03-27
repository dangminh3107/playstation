<template>
  <div class="explore">
    <div class="header">
      <h1>Explore PlayStation®4</h1>
      <h2>
        Incredible games, non-stop entertainment. There's never been a better time to enjoy PS4.
      </h2>
    </div>
    <div class="carousel">
      <div class="grid">
        <VueSlickCarousel v-bind="settings">
          <div class="item" v-for="(item, index) in arrData" :key="index">
            <div class="image">
              <img :src="require(`@/assets/images/explore/${item.image}`)" alt="" />
            </div>
            <div class="text">
              <h1>{{ item.title }}</h1>
              <span>{{ item.overview }}</span>
            </div>
            <div class="button">
              <button>{{ item.button }}</button>
            </div>
          </div>
        </VueSlickCarousel>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'ExploreComponent',
  data() {
    return {
      settings: {
        dots: false,
        arrows: false,
        dotsClass: 'slick-dots custom-dot-class',
        edgeFriction: 0.35,
        infinite: true,
        speed: 500,
        slidesToShow: 3,
        slidesToScroll: 1,
        responsive: [
          {
            breakpoint: 1024,
            settings: {
              slidesToShow: 2,
              slidesToScroll: 1,
              infinite: true,
              arrows: true,
              dots: true,
              dotsClass: 'slick-dots custom-dot-class',
              edgeFriction: 0.35,
              speed: 500,
            },
          },
          {
            breakpoint: 760,
            settings: {
              slidesToShow: 2,
              slidesToScroll: 1,
              initialSlide: 1,
              arrows: false,
              dots: true,
              dotsClass: 'slick-dots custom-dot-class',
              edgeFriction: 0.35,
              speed: 500,
            },
          },
          {
            breakpoint: 600,
            settings: {
              slidesToShow: 1,
              slidesToScroll: 1,
              arrows: false,
              dots: true,
              dotsClass: 'slick-dots custom-dot-class',
              edgeFriction: 0.35,
              speed: 500,
            },
          },
        ],
      },
      arrData: [
        {
          image: 'img_49.jpg',
          title: 'PlayStation 4',
          overview: 'Incredible games live on PS4, with 1TB storage.',
          button: 'Learn more',
        },
        {
          image: 'img_50.jpg',
          title: 'PlayStation VR',
          overview: 'Over 500 games and experiences and counting. See them all.',
          button: 'Learn more',
        },
        {
          image: 'img_51.jpg',
          title: 'Accessories',
          overview: 'Enhance your PS4 experience with a range of official accessories.',
          button: 'Learn more',
        },
      ],
    };
  },
};
</script>

<style lang="scss" scoped>
.explore {
  display: flex;
  width: 100%;
  justify-content: center;
  align-items: center;
  flex-direction: column;
  padding: 100px 0;
  overflow: hidden;
  .header {
    display: flex;
    text-align: center;
    flex-direction: column;
    margin-bottom: 60px;
    h1 {
      font-size: 4rem;
      font-weight: 400;
      margin-bottom: 20px;
    }
    h2 {
      font-size: 2.2rem;
      color: var(--grey);
      font-weight: 400;
    }
  }
  .carousel {
    width: 100%;
    display: flex;
    justify-content: center;
    @media screen and (max-width: 1280px) {
      padding-left: 40px;
    }
    .grid {
      max-width: 1200px;
      width: 100%;
      .item {
        display: flex;
        flex-direction: column;
        padding-right: 20px;
        .image {
          height: 218px;
          display: block;
          img {
            height: 100%;
            width: 100%;
            display: block;
            object-position: center;
            object-fit: contain;
          }
        }
        .text {
          display: flex;
          flex-direction: column;
          h1 {
            font-size: 4rem;
            font-weight: 400;
          }
          span {
            font-size: 2rem;
            color: var(--light-text);
            padding: 10px 0 20px;
          }
        }
        .button {
          font-size: 1.8rem;
          line-height: 1.8rem;
          margin-left: 4px;
          margin-bottom: 4px;
          button {
            outline: 2px solid var(--main-color);
            border: none;
            border-radius: 20px;
            color: var(--white-color);
            background: var(--main-color);
            padding: 5px 15px 8px;
            font-weight: 500;
            &:hover {
              outline-offset: 3px;
            }
          }
        }
      }
    }
  }
}
</style>
