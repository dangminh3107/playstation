<template>
  <div class="product">
    <div class="grid-1320">
      <div class="header">
        <h1>{{ myData.h1 }}</h1>
        <h2>{{ myData.h2 }}</h2>
      </div>
      <div class="list-product">
        <div class="product-item" v-for="(item, index) in myData.list" :key="index">
          <div class="product-img">
            <img :src="require(`@/assets/images/ps4view/product/${item.image}`)" alt="" />
          </div>
          <div class="product-detail">
            <h1>{{ item.name }}</h1>
            <span>{{ item.overview }}</span>
            <p>{{ item.sub }}</p>
          </div>
        </div>
      </div>
      <div class="button">
        <button>Buy now</button>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'ProductHardwareComponent',
  props: ['dataArr'],
  data() {
    return {
      myData: this.dataArr,
      isShow: false,
    };
  },
  watch: {
    isShow() {
      this.$emit('isShowChange', this.isShow);
    },
  },
};
</script>

<style lang="scss" scoped>
.product {
  display: flex;
  justify-content: center;
  .grid-1320 {
    max-width: 1320px;
    width: 100%;
    display: flex;
    flex-direction: column;
    align-items: center;
    .header {
      display: flex;
      flex-direction: column;
      justify-content: center;
      align-items: center;
      h1 {
        font-size: 5rem;
        line-height: 5rem;
        color: var(--main-color);
        font-weight: 400;
        padding: 86px 0 30px;
      }
      h2 {
        font-size: 2rem;
        font-weight: 400;
        color: rgba(31, 31, 31, 0.7);
      }
      @media screen and (max-width: 680px) {
        padding: 0 30px;
        h1 {
          font-size: 7vw;
          text-align: center;
        }
        h2 {
          text-align: center;
        }
      }
    }
    .list-product {
      display: grid;
      grid-template-columns: 1fr 1fr;
      column-gap: 50px;
      @media screen and (max-width: 680px) {
        grid-template-columns: 1fr;
        row-gap: 50px;
      }
      .product-item {
        .product-img {
          padding: 70px 100px 100px;
          img {
            width: 100%;
            object-fit: contain;
          }
        }
        .product-detail {
          display: flex;
          flex-direction: column;
          align-items: center;
          h1 {
            font-size: 4rem;
            line-height: 4rem;
            color: var(--main-color);
            font-weight: 400;
          }
          span {
            font-size: 1.6rem;
            color: var(--light-text);
            opacity: 0.7;
            margin: 40px 0 30px;
          }
          p {
            font-size: 1.2rem;
          }
        }
      }
    }
    .button {
      margin: 60px 0;
      button {
        padding: 12px 22px;
        font-size: 1.6rem;
        line-height: 1.6rem;
        background: var(--firebrick);
        color: var(--white-color);
        font-weight: bold;
        border: none;
        border-radius: 20px;
        transition: all 0.5s ease-in-out;
        &:hover {
          outline: 3px solid var(--firebrick);
          outline-offset: 3px;
        }
      }
    }
  }
}
</style>
