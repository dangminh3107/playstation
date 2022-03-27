<template>
  <div class="entertainment">
    <div class="grid">
      <div class="text">
        <h1>{{ data.title }}</h1>
        <p>{{ data.overview }}</p>
      </div>
      <div class="img">
        <img :src="require(`@/assets/images/ps4view/${data.image}`)" alt="" />
      </div>
      <button>{{ data.contentBtn }}</button>
    </div>
  </div>
</template>

<script>
export default {
  name: 'EntertaimentComponent',
  props: ['dataArr'],
  data() {
    return {
      data: this.dataArr,
    };
  },
};
</script>

<style lang="scss" scoped>
.entertainment {
  display: flex;
  align-items: center;
  justify-content: center;
  background: #1f1f1f;
  .grid {
    max-width: 1320px;
    width: 100%;
    height: 100%;
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: space-around;
    padding: 50px 20px;
    text-align: center;
    .text {
      h1 {
        font-size: 4rem;
        line-height: 4rem;
        font-weight: 400;
        color: var(--white-color);
        @media screen and (max-width: 640px) {
          font-size: 6.5vw;
        }
      }
      p {
        font-size: 1.7rem;
        line-height: 1.7rem;
        color: var(--white-color);
        margin: 30px 0 40px;
        @media screen and (max-width: 640px) {
          font-size: 3vw;
        }
      }
    }
    .img {
      width: 83%;
      img {
        width: 100%;
        object-fit: contain;
      }
    }
    button {
      padding: 6px 15px 8px;
      border: none;
      font-size: 1.7rem;
      font-weight: bold;
      border-radius: 20px;
      background: #212328;
      color: #00b0ff;
      margin-top: 30px;
      &:hover {
        outline: 3px solid #363a41;
        outline-offset: 3px;
      }
      @media screen and (max-width: 640px) {
        font-size: 3vw;
      }
    }
  }
}
</style>
