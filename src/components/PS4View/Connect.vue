<template>
  <!-- eslint-disable max-len -->
  <b-container class="connect-wrapper">
    <b-row>
      <b-col cols="12" class="text-center connect-header">
        <h1>{{ data.title }}</h1>
        <h2>{{ data.subTitle }}</h2>
      </b-col>
      <b-row class="justify-content-center content-row">
        <b-col sm="11" md="6">
          <b-col class="remote-item" cols="12">
            <div class="header">
              <h1>{{ data.remoteTitle }}</h1>
              <h2>{{ data.remoteSubTitle }}</h2>
            </div>
            <button>{{ data.remoteBtn }}</button>
          </b-col>
        </b-col>
        <b-col sm="11" md="6">
          <b-col cols="12">
            <div class="image-remote">
              <img :src="require(`@/assets/images/ps4view/${data.remoteImg}`)" alt="" />
            </div>
          </b-col>
        </b-col>
      </b-row>
      <b-row class="content-guide justify-content-center">
        <b-col lg="8" md="10" sm="12">
          <div class="grid-guide">
            <div class="guide-item" v-for="(item, index) in data.list" :key="index">
              <div class="guide-img">
                <img :src="require(`@/assets/images/ps4view/${item.image}`)" alt="" />
              </div>
              <h1>{{ item.title }}</h1>
              <h2>{{ item.overview }}</h2>
            </div>
          </div>
          <div class="button">
            <button>{{ data.btn }}</button>
          </div>
        </b-col>
      </b-row>
    </b-row>
  </b-container>
</template>

<script>
export default {
  // eslint-disable-next-line quotes
  name: "ConnectComponent",
  // eslint-disable-next-line quotes
  props: ["dataArr"],
  data() {
    return {
      data: this.dataArr,
    };
  },
};
</script>

<style lang="scss" scoped>
.connect-wrapper {
  padding: 50px 0;
  max-width: 1320px !important;
  overflow: hidden;
  .connect-header {
    h1 {
      color: var(--main-color);
      font-size: 4rem;
      line-height: 4rem;
      font-weight: 400;
      @media screen and (max-width: 768px) {
        font-size: 5vw;
      }
    }
    h2 {
      font-size: 2rem;
      font-weight: 400;
      color: rgba(31, 31, 31, 0.6);
      margin: 40px 0;
    }
  }
  .content-row {
    @media screen and (max-width: 767px) {
      flex-wrap: wrap-reverse !important;
    }
    .remote-item {
      display: flex;
      flex-direction: column;
      justify-content: center;
      height: 100%;
      align-items: start;
      @media screen and (max-width: 575px) {
        align-items: center;
        text-align: center;
      }
      .header {
        h1 {
          font-size: 3rem;
          font-weight: 300;
        }
        h2 {
          font-size: 1.6rem;
          line-height: 2.2rem;
          font-weight: 400;
          color: rgba(31, 31, 31, 0.6);
          margin: 30px 0;
        }
        @media screen and (max-width: 1319px) {
          margin: 20px 20px 0 20px;
        }
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
        @media screen and (max-width: 1319px) {
          margin: 0 20px 20px 20px;
        }
      }
    }
    .image-remote {
      display: flex;
      width: 100%;
      justify-content: center;
      align-items: center;
      img {
        width: 65%;
        object-fit: contain;
        @media screen and (max-width: 1319px) {
          padding: 20px;
        }
      }
    }
  }
  .content-guide {
    margin-top: 70px;
    margin-left: 0 !important;
    margin-right: 0 !important;
    .grid-guide {
      display: grid;
      width: 100%;
      grid-template-columns: repeat(4, 1fr);
      column-gap: 10px;
      row-gap: 10px;
      @media screen and (max-width: 720px) {
        grid-template-columns: 1fr;
        padding: 0 20px;
      }
      .guide-item {
        text-align: center;
        .guide-img {
          img {
            width: 70%;
            object-fit: contain;
            @media screen and (max-width: 720px) {
              width: 10%;
            }
          }
        }
        h1 {
          font-size: 2.5rem;
          line-height: 2.5rem;
          font-weight: 400;
          margin: 30px 0;
        }
        h2 {
          font-size: 1.8rem;
          color: rgba(31, 31, 31, 0.6);
          font-weight: 400;
        }
      }
    }
    .button {
      margin-top: 50px;
      display: flex;
      justify-content: center;
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
        @media screen and (max-width: 1319px) {
          margin: 0 20px 20px 20px;
        }
      }
    }
  }
}
</style>
