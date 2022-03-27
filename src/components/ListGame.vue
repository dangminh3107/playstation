<template>
  <div class="game-wrapper">
    <VueSlickCarousel v-bind="settings" ref="carouselListGame">
      <div class="grid-contain" v-for="(block, index) in blockContent" :key="index" ref="myRef">
        <div class="grid-title">
          <h1>{{ block.title }}</h1>
          <h2>{{ block.subTitle }}</h2>
        </div>
        <div class="grid-list">
          <div class="item" v-for="(item, idx) in block.list" :key="idx">
            <div class="img">
              <img :src="require(`@/assets/images/${item.image}`)" alt="" />
            </div>
            <div class="text">
              <span>{{ item.name }}</span>
            </div>
          </div>
        </div>
      </div>
    </VueSlickCarousel>
    <div class="button-control">
      <button ref="prevBtn" @click="handleClickPrev">
        <font-awesome-icon icon="fa-solid fa-angle-left" />
      </button>
      <button ref="nextBtn" @click="handleClickNext">
        <font-awesome-icon icon="fa-solid fa-angle-right" />
      </button>
    </div>
    <div class="layer-left" ref="layerLeft"></div>
    <div class="layer-right active" ref="layerRight"></div>
  </div>
</template>

<script>
export default {
  name: 'ListGameComponent',
  data() {
    return {
      settings: {
        dots: false,
        arrows: false,
        dotsClass: 'slick-dots custom-dot-class',
        edgeFriction: 0.35,
        infinite: true,
        speed: 500,
        slidesToShow: 1,
        slidesToScroll: 1,
      },
      blockContent: [
        {
          title: 'New releases',
          subTitle: 'Great PS5 and PS4 games available now',
          list: [
            {
              image: 'new_release/img_25.jpg',
              name: 'Horizon Forbidden West',
            },
            {
              image: 'new_release/img_26.jpg',
              name: 'Elden Ring',
            },
            {
              image: 'new_release/img_27.jpg',
              name: 'UNCHARTED™: Legacy of Thieves Collection',
            },
            {
              image: 'new_release/img_28.jpg',
              name: "Marvel's Guardians of the Galaxy",
            },
            {
              image: 'new_release/img_29.jpg',
              name: 'Sifu',
            },
            {
              image: 'new_release/img_30.jpg',
              name: 'Dying Light 2 Stay Human',
            },
            {
              image: 'new_release/img_31.jpg',
              name: 'DEATHLOOP',
            },
            {
              image: 'new_release/img_32.jpg',
              name: 'EA SPORTS™ FIFA 22',
            },
            {
              image: 'new_release/img_33.jpg',
              name: 'Tom Clancy’s Rainbow Six Extraction',
            },
            {
              image: 'new_release/img_34.jpg',
              name: 'Gran Turismo® 7',
            },
            {
              image: 'new_release/img_35.jpg',
              name: 'Gran Turismo® 7',
            },
            {
              image: 'new_release/img_36.jpg',
              name: 'Stranger of Paradise Final Fantasy Origin',
            },
          ],
        },
        {
          title: 'Coming soon',
          subTitle: 'Amazing new experiences are just around the corner',
          list: [
            {
              image: 'coming_soon/img_37.jpg',
              name: "Teenage Mutant Ninja Turtles: Shredder's Revenge",
            },
            {
              image: 'coming_soon/img_38.jpg',
              name: "Tiny Tina's Wonderlands",
            },
            {
              image: 'coming_soon/img_39.jpg',
              name: 'Saints Row',
            },
            {
              image: 'coming_soon/img_40.jpg',
              name: 'Gotham Knights',
            },
            {
              image: 'coming_soon/img_41.jpg',
              name: 'Forspoken',
            },
            {
              image: 'coming_soon/img_42.jpg',
              name: 'Vampire: The Masquerade - Bloodhunt',
            },
            {
              image: 'coming_soon/img_43.jpg',
              name: 'Little Devil Inside',
            },
            {
              image: 'coming_soon/img_44.jpg',
              name: 'Stray',
            },
            {
              image: 'coming_soon/img_45.jpg',
              name: 'Suicide Squad: Kill the Justice League',
            },
            {
              image: 'coming_soon/img_46.jpg',
              name: 'Ghostwire: Tokyo',
            },
            {
              image: 'coming_soon/img_47.jpg',
              name: 'God of War Ragnarök',
            },
            {
              image: 'coming_soon/img_48.jpg',
              name: 'LEGO Star Wars: The Skywalker Saga',
            },
          ],
        },
      ],
    };
  },
  methods: {
    handleClickPrev() {
      console.log(true);
      this.$refs.carouselListGame.prev();
      this.$refs.layerRight.classList.remove('active');
      setTimeout(() => {
        this.$refs.layerRight.classList.add('active');
      }, 500);
    },
    handleClickNext() {
      this.$refs.carouselListGame.next();
      this.$refs.layerRight.classList.remove('active');
      setTimeout(() => {
        this.$refs.layerRight.classList.add('active');
      }, 500);
    },
  },
};
</script>

<style lang="scss">
.game-wrapper {
  display: grid;
  grid-template-columns: 88% 88%;
  white-space: nowrap;
  overflow: hidden;
  background-color: var(--light-text);
  position: relative;
  .slick-slider {
    .slick-list {
      overflow: unset !important;
      .grid-contain {
        max-width: 1300px;
        width: 100%;
        display: flex;
        flex-direction: column;
        position: relative;
        left: 6%;
        padding: 40px 0 30px;
        transition: transform 1s ease;
        .grid-title {
          color: var(--white-color);
          h1 {
            font-size: 1.6rem;
            font-weight: bold;
          }
          h2 {
            margin: 10px 0 40px;
            font-size: 2.2rem;
            font-weight: 400;
            @media screen and (max-width: 760px) {
              max-width: 68%;
              font-size: 3vw;
              white-space: pre-wrap;
            }
          }
        }
        .grid-list {
          display: grid;
          grid-template-columns: repeat(auto-fit, 190px);
          grid-template-rows: repeat(auto-fit, 270px);
          column-gap: 30px;
          .item {
            cursor: pointer;
            width: 100%;
            display: flex;
            flex-direction: column;
            .img {
              width: 100%;
              height: 192px;
              border-radius: 10px;
              overflow: hidden;
              transition: all 0.5s ease;
              &:hover {
                transform: scale(1.02);
              }
              img {
                width: 100%;
                height: 100%;
                /* object-fit: contain; */
                object-position: center;
              }
            }
            .text {
              font-size: 1.7rem;
              white-space: pre-wrap;
              padding: 10px 5px;
              color: var(--white-color);
              span {
              }
            }
          }
        }
      }
    }
  }
  .button-control {
    position: absolute;
    right: 10%;
    top: 50px;
    button {
      font-size: 2.2rem;
      line-height: 2rem;
      outline: 2px solid var(--white-color);
      padding: 12px 18px 12px;
      border: none;
      border-radius: 50%;
      margin: 0 5px;
      &:hover {
        outline-offset: 3px;
      }
    }
  }
  .layer-left,
  .layer-right {
    position: absolute;
  }
  .layer-left {
    position: absolute;
    left: 0;
    top: 0;
    bottom: 0;
    width: 5%;
    background: var(--light-text);
    z-index: 55;
  }
  .layer-right {
    position: absolute;
    right: 0;
    top: 0;
    bottom: 0;
    width: 8%;
    background: rgba(31, 31, 31, 0.6);
    z-index: 55;
    opacity: 0;
    &.active {
      animation: fadeLayer 0.4s linear forwards;
    }
  }
}
</style>
