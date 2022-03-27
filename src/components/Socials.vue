<template>
  <div class="socials-wrapper">
    <div class="socials-grid">
      <h1>{{ headText }}</h1>
      <div class="social-media">
        <div class="social-item" v-for="(item, index) in socialsArr" :key="index">
          <img :src="require(`@/assets/images/social/${item}`)" alt="" />
        </div>
      </div>
      <div class="text-footer">
        <h3>{{ footText }}</h3>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'SocialsComponent',
  data() {
    return {
      headText: 'Follow us on social media',
      socialsArr: ['img_56.jpg', 'img_57.jpg', 'img_58.jpg', 'img_59.jpg'],
      footText:
        '* PS5 console, console cover, and DualSense wireless controller sold separately. Midnight Black and Cosmic Red covers now available. Other covers colors coming in 2022.',
    };
  },
};
</script>

<style lang="scss" scoped>
.socials-wrapper {
  display: flex;
  justify-content: center;
  padding: 60px 0 70px;
  .socials-grid {
    max-width: 1320px;
    width: 100%;
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    h1 {
      font-size: 3.3rem;
      font-weight: 400;
    }
    .social-media {
      width: 100%;
      justify-content: center;
      display: grid;
      padding: 90px 0 208px;
      grid-template-columns: repeat(auto-fit, 114px);
      column-gap: 33px;
      row-gap: 33px;
      .social-item {
        border-radius: 10px;
        cursor: pointer;
        overflow: hidden;
        width: 100%;
        transition: all 0.4s ease;
        &:hover {
          transform: scale(1.02);
        }
        img {
          width: 100%;
          object-fit: contain;
        }
      }
    }
    .text-footer {
      @media screen and (max-width: 760px) {
        text-align: center;
      }
      h3 {
        font-size: 1.7rem;
        line-height: 2.6rem;
        font-weight: 400;
      }
    }
  }
}
</style>
