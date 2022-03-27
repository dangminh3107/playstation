<template>
  <div class="experience">
    <div class="exp-item">
      <div class="exp-content">
        <h2>THIS MONTH</h2>
        <h1>ON PLAYSTATION</h1>
        <p>Check out this month's biggest release along with dedicated features, guides and more</p>
        <button>Find out more</button>
      </div>
    </div>
    <div class="exp-guide">
      <div class="grid-1320">
        <div class="guide-item" v-for="(item, index) in arrData" :key="index">
          <div>
            <img :src="require(`@/assets/images/banner_2/${item.img}`)" alt="" />
          </div>
          <span class="text">{{ item.text }}</span>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'ExperienceComponent',
  data() {
    return {
      arrData: [
        {
          img: 'img_20.jpg',
          text: "Best arcade-style shoot 'em ups on PS4 and PS5",
        },
        {
          img: 'img_21.jpg',
          text: 'How Gran Turismo 7 harnesses the power of PS5',
        },
        {
          img: 'img_22.jpg',
          text: 'How to survive your first few hours in Elden Ring',
        },
      ],
    };
  },
};
</script>

<style lang="scss" scoped>
.experience {
  @media screen and (max-width: 760px) {
    min-height: 900px;
  }
  .exp-item {
    background-image: url("../assets/images/banner_2/img_19.jpg");
    background-repeat: no-repeat;
    background-position: center;
    background-size: cover;
    transition: all 0.5s ease;
    @media screen and (max-width: 760px) {
      background-image: url("../assets/images/banner_2/img_19_800.jpg");
    }
    .exp-content {
      position: relative;
      left: 6%;
      padding: 60px 0 160px;
      max-width: 570px;
      color: var(--white-color);
      @media screen and (max-width: 760px) {
        max-width: 100%;
        width: 100%;
        display: flex;
        flex-direction: column;
        justify-content: center;
        align-items: center;
        position: unset;
        text-align: center;
      }
      h2,
      h1 {
        font-size: 4rem;
      }
      h1 {
        font-weight: bold;
      }
      h2 {
        font-weight: normal;
      }
      p {
        margin: 38px 0;
        font-size: 2rem;
        color: var(--white-text);
        opacity: 0.7;
      }
      button {
        font-size: 1.6rem;
        line-height: 1.6rem;
        font-weight: bold;
        padding: 10px 15px 12px;
        border: none;
        border-radius: 20px;
        outline: 2.5px solid var(--white-color);
        &:hover {
          outline-offset: 3px;
        }
      }
    }
  }
  .exp-guide {
    display: flex;
    justify-content: center;
    background-color: var(--dark-purple);
    padding-bottom: 50px;
    max-height: 280px;
    @media screen and (max-width: 1360px) and (min-width: 769px) {
      max-height: unset;
    }
    @media screen and (max-width: 760px) {
      max-height: fit-content;
    }
    .grid-1320 {
      display: grid;
      grid-template-columns: repeat(auto-fit, 400px);
      column-gap: 60px;
      max-width: 1320px;
      width: 100%;
      position: relative;
      top: -108px;
      @media screen and (max-width: 1360px) and (min-width: 769px) {
        row-gap: 60px;
        justify-content: center;
      }
      @media screen and (max-width: 760px) {
        justify-content: center;
        row-gap: 30px;
        top: 0;
      }
      .guide-item {
        width: 100%;
        display: flex;
        flex-direction: column;
        cursor: pointer;
        div {
          box-shadow: 0 5px 10px var(--black-color);
          width: 100%;
          border-radius: 20px;
          transition: all 0.5s ease;
          &:hover {
            box-shadow: 0 5px 15px var(--black-color);
            transform: scale(1.02);
          }
          img {
            border-radius: 20px;
            width: 100%;
            object-fit: contain;
          }
        }
        span {
          padding-top: 20px;
          font-size: 2.5rem;
          text-align: center;
          color: var(--white-color);
        }
      }
    }
  }
}
</style>
