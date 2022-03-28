<template>
  <b-container class="f-container">
    <b-row class="f-row">
      <b-col md="8" class="f-header">
        <h1>{{ data.title }}</h1>
        <p>{{ data.overview }}</p>
      </b-col>
    </b-row>
    <b-row class="f-list">
      <b-col xl="12" lg="8" md="8" sm="10">
        <div class="grid-list">
          <div class="item" v-for="(item, index) in list" :key="index">
            <div class="img-contain">
              <img :src="require(`@/assets/images/ps4view/${item.image}`)" alt="" />
            </div>
            <h1>{{ item.title }}</h1>
            <p>{{ item.overview }}</p>
            <button>{{ item.btn }}</button>
          </div>
        </div>
        <div class="f-new">
          <div class="image-new">
            <img :src="require(`@/assets/images/ps4view/${data.new.image}`)" alt="" />
          </div>
          <div class="content-wrapper">
            <div class="content">
              <h1>{{ data.new.title }}</h1>
              <p>{{ data.new.overview }}</p>
              <button>{{ data.new.btn }}</button>
            </div>
          </div>
        </div>
      </b-col>
    </b-row>
  </b-container>
</template>

<script>
export default {
  // eslint-disable-next-line quotes
  name: "FamilyComponent",
  // eslint-disable-next-line quotes
  props: ["dataArr"],
  data() {
    return {
      data: this.dataArr,
      list: this.dataArr.list,
    };
  },
};
</script>

<style lang="scss" scoped>
.f-container {
  padding: 100px 0;
  max-width: 1320px !important;
  overflow: hidden;
  .f-row {
    display: flex;
    justify-content: center;
    @media screen and (max-width: 768px) {
      margin-left: 0;
      margin-right: 0;
    }
    .f-header {
      display: flex;
      flex-direction: column;
      justify-content: center;
      @media screen and (max-width: 768px) {
        padding: 0 20px;
      }
      h1 {
        font-size: 4rem;
        font-weight: 400;
        color: var(--main-color);
        text-align: center;
      }
      p {
        font-size: 1.7rem;
        text-align: center;
        margin: 36px 0 46px;
      }
    }
  }
  .f-list {
    justify-content: center;
    .grid-list {
      display: grid;
      grid-template-columns: repeat(2, 1fr);
      column-gap: 50px;
      row-gap: 50px;
      padding: 0 20px;
      @media screen and (max-width: 768px) {
        display: flex;
        flex-direction: column;
      }
      .item {
        .img-contain {
          img {
            width: 100%;
            object-fit: contain;
          }
        }
        h1 {
          font-size: 2.5rem;
          font-weight: 400;
          color: var(--main-color);
          margin: 20px 0;
        }
        p {
          font-size: 1.6rem;
          color: rgba(31, 31, 31, 0.7);
        }
        button {
          margin-top: 10px;
          padding: 6px 15px 7px;
          font-size: 1.5rem;
          font-weight: bold;
          border: none;
          color: #fff;
          background: var(--main-color);
          border-radius: 20px;
          &:hover {
            outline: 3px solid var(--main-color);
            outline-offset: 3px;
          }
        }
      }
    }
    .f-new {
      margin-top: 50px;
      display: grid;
      grid-template-columns: repeat(2, 1fr);
      padding: 0 20px;
      column-gap: 50px;
      row-gap: 50px;
      @media screen and (max-width: 768px) {
        display: flex;
        flex-direction: column;
      }
      .image-new {
        img {
          width: 100%;
          object-fit: contain;
        }
      }
      .content-wrapper {
        display: flex;
        align-items: center;
        .content {
          display: flex;
          flex-direction: column;
          align-items: start;
          h1 {
            font-size: 2.5rem;
            font-weight: 400;
            color: var(--main-color);
            margin: 20px 0;
          }
          p {
            font-size: 1.6rem;
            color: rgba(31, 31, 31, 0.7);
          }
          button {
            padding: 6px 15px 7px;
            font-size: 1.5rem;
            font-weight: bold;
            border: none;
            color: var(--main-color);
            background: #dfe1e3;
            border-radius: 20px;
            &:hover {
              outline: 3px solid #afafaf;
              outline-offset: 3px;
            }
          }
        }
      }
    }
  }
}
</style>
