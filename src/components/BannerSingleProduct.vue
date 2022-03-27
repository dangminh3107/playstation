<template>
  <div class="single-wrapper">
    <div class="header">
      <h1>{{ data.h1 }}</h1>
      <h3>{{ data.h3 }}</h3>
    </div>
    <div class="single-product">
      <div class="image">
        <img :src="require(`@/assets/images/ps4view/product/${data.image}`)" alt="" />
      </div>
      <div class="overview">
        <h2>{{ data.title }}</h2>
        <p>{{ data.overview }}</p>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'BannerSingleProductComponent',
  props: ['dataArr'],
  data() {
    return {
      data: this.dataArr,
    };
  },
};
</script>

<style lang="scss" scoped>
.single-wrapper {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  overflow: hidden;
  width: 100%;
  .header {
    display: flex;
    flex-direction: column;
    align-items: center;
    @media screen and (max-width: 1024px) {
      text-align: center;
      padding-left: 20px;
      padding-right: 20px;
    }
    h1 {
      font-size: 4rem;
      line-height: 4rem;
      font-weight: 400;
      color: var(--main-color);
      padding: 80px 0 30px;
      @media screen and (max-width: 1024px) {
        font-size: 4vw;
      }
      @media screen and (max-width: 768px) {
        font-size: 6vw;
      }
    }
    h3 {
      font-size: 2rem;
      line-height: 2.6rem;
      color: rgba(31, 31, 31, 0.6);
      font-weight: 400;
      max-width: 840px;
      text-align: center;
    }
  }
  .single-product {
    padding: 100px 0 70px;
    width: 100%;
    display: grid;
    grid-template-columns: 60% 42%;
    column-gap: 50px;
    row-gap: 50px;
    position: relative;
    left: -10%;
    @media screen and (max-width: 1024px) and (min-width: 761px) {
      grid-template-columns: 1fr 1fr;
      position: unset;
      padding: 100px 30px 70px;
    }
    @media screen and (max-width: 760px) {
      grid-template-columns: 1fr;
      position: unset;
      padding: 100px 20px 70px;
    }
    .image {
      img {
        width: 100%;
        object-fit: contain;
      }
    }
    .overview {
      display: flex;
      flex-direction: column;
      justify-content: center;
      h2 {
        font-size: 3rem;
        line-height: 3rem;
        font-weight: 400;
      }
      p {
        margin-top: 20px;
        font-size: 1.8rem;
        line-height: 3rem;
        color: rgba(31, 31, 31, 0.6);
      }
    }
  }
}
</style>
