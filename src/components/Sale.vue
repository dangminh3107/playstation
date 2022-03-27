<template>
  <div class="sale-wrapper">
    <div class="sale-grid">
      <div class="content-wrapper">
        <div class="content">
          <h1>{{ headerText }}</h1>
          <p>{{ overview }}</p>
          <button>{{ button }}</button>
        </div>
      </div>
      <div class="image">
        <img :src="img51" alt="" />
      </div>
    </div>
  </div>
</template>

<script>

import img51 from '../assets/images/mockup/img 51.jpg';

export default {
  name: 'SaleComponent',
  data() {
    return {
      headerText: 'New savings on PlayStation Store',
      overview:
        'Deep discounts, curated collections and seasonal sales on PS5, PS4 and PS VR hits, all in one place.',
      button: 'See all deals',
      img51,
    };
  },
};
</script>

<style lang="scss" scoped>
.sale-wrapper {
  display: flex;
  align-items: center;
  padding: 40px 0;
  width: 100%;
  justify-content: center;
  .sale-grid {
    max-width: 1320px;
    width: 100%;
    display: grid;
    grid-template-columns: 30% 65%;
    justify-content: space-between;
    column-gap: 50px;
    padding: 0 20px;
    @media screen and (max-width: 760px) {
      display: flex;
      flex-direction: column-reverse;
      padding: 0 30px;
    }
    .content-wrapper {
      display: flex;
      flex-direction: column;
      align-items: center;
      justify-content: center;
      .content {
        @media screen and (max-width: 760px) {
          text-align: center;
          margin-top: 30px;
        }
        h1 {
          font-size: 4rem;
          font-weight: 400;
        }
        p {
          font-size: 2rem;
          color: var(--light-text);
          opacity: 0.7;
          margin: 20px 0 40px;
        }
        button {
          border: none;
          border-radius: 20px;
          font-size: 1.8rem;
          background: var(--main-color);
          font-weight: bold;
          color: var(--white-color);
          padding: 5px 12px 6px;
          transition: all 0.4s ease;
          &:hover {
            outline: 3px solid var(--main-color);
            outline-offset: 3px;
          }
        }
      }
    }
    .image {
      border-radius: 10px;
      cursor: pointer;
      overflow: hidden;
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
}
</style>
