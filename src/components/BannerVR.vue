<template>
  <div
    class="banner-v2"
    :style="{
      backgroundImage:
        'url(' + require(`@/assets/images/ps4view/banner_2/${data.background}`) + ')',
    }"
  >
    <div class="grid-990">
      <header v-bind:style="{ background: data.colorHead }">
        <h1>{{ data.header }}</h1>
        <p>{{ data.subHead }}</p>
      </header>
      <div class="img-overlay">
        <img :src="require(`@/assets/images/ps4view/banner_2/${data.overlay}`)" alt="" />
      </div>
      <div class="btn">
        <button
          :style="{ background: data.colorBtn, color: data.colorText, '--color': data.colorBtn }"
        >
          {{ data.btn }}
        </button>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'BannerStaticV2Component',
  props: ['dataArr'],
  data() {
    return {
      data: this.dataArr,
    };
  },
};
</script>

<style lang="scss" scoped>
.banner-v2 {
  background-repeat: no-repeat;
  background-size: cover;
  background-position: center;
  display: flex;
  justify-content: center;
  padding: 80px 20px;
  .grid-990 {
    max-width: 990px;
    width: 100%;
    display: flex;
    flex-direction: column;
    align-items: center;
    header {
      max-width: 90%;
      display: flex;
      flex-direction: column;
      align-items: center;
      padding: 24px;
      h1 {
        font-size: 4rem;
        font-weight: 400;
        margin-bottom: 30px;
        @media screen and (max-width: 680px) {
          font-size: 6vw;
        }
      }
      p {
        font-size: 1.7rem;
        text-align: center;
        @media screen and (max-width: 680px) {
          font-size: 3vw;
        }
      }
    }
    .img-overlay {
      width: 100%;
      margin-top: 90px;
      img {
        width: 100%;
        object-fit: contain;
      }
    }
    .btn {
      button {
        font-size: 1.8rem;
        font-weight: bold;
        padding: 5px 15px;
        border: none;
        border-radius: 20px;
        cursor: pointer;
        &:hover {
          outline: 3px solid var(--color);
          outline-offset: 3px;
        }
      }
    }
  }
}
</style>
