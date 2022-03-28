<template>
  <!-- eslint-disable max-len -->
  <div class="experience-contain">
    <b-img
      :src="require(`@/assets/images/ps4view/${data.background}`)"
      fluid
      class="exp-img"
      v-if="!isShow"
    ></b-img>
    <b-img
      :src="require(`@/assets/images/ps4view/${data.backgroundMobile}`)"
      fluid
      class="exp-img"
      v-else
    ></b-img>
    <b-container class="content-overlay">
      <b-col md="12">
        <div class="grid-content">
          <div class="grid-item">
            <div class="grid-item-img">
              <img :src="require(`@/assets/images/ps4view/${data.image}`)" alt="" />
              <div class="button">
                <button>{{ data.btn }}</button>
              </div>
            </div>
          </div>
          <div class="grid-item">
            <div class="text-box">
              <h1>{{ data.title }}</h1>
              <p>{{ data.overview }}</p>
            </div>
          </div>
        </div>
      </b-col>
    </b-container>
  </div>
</template>

<script>
export default {
  // eslint-disable-next-line quotes
  name: "PS4ExperienceComponent",
  // eslint-disable-next-line quotes
  props: {
    dataArr: {
      type: Object,
      require: true,
    },
    sizeWidth: {
      type: Number,
      require: false,
    },
  },
  data() {
    return {
      data: this.dataArr,
      isShow: false,
    };
  },
  mounted() {
    if (window.innerWidth < 768) this.isShow = true;
    else this.isShow = false;
  },
  watch: {
    sizeWidth(val) {
      if (val < 768) this.isShow = true;
      else this.isShow = false;
    },
  },
};
</script>

<style lang="scss" scoped>
.experience-contain {
  overflow: hidden;
  position: relative;
  .exp-img {
    max-width: 140%;
    min-height: 514px;
    @media screen and (max-width: 768px) {
      min-height: 720px;
    }
  }
  .content-overlay {
    position: absolute;
    display: flex;
    align-items: end;
    height: 86.9%;
    top: 0;
    left: 0;
    right: 0;
    max-width: 1320px !important;
    @media screen and (max-width: 768px) {
      height: 100%;
      align-items: center;
    }
    .grid-content {
      display: grid;
      grid-template-columns: repeat(2, 1fr);
      column-gap: 30px;
      row-gap: 30px;
      @media screen and (max-width: 768px) {
        display: flex;
        flex-direction: column-reverse;
        padding: 20px 0 60px;
      }
      .grid-item {
        position: relative;
        .grid-item-img {
          position: relative;
          img {
            width: 100%;
            object-fit: contain;
          }
          .button {
            position: absolute;
            bottom: -10%;
            transform: translateY(100%);
            @media screen and (max-width: 768px) {
              position: unset;
              transform: unset;
              margin-top: 30px;
            }
            button {
              border-radius: 20px;
              border: none;
              padding: 5px 14px 6px;
              font-size: 1.5rem;
              background: #2d64e6;
              color: #fff;
              font-weight: bold;
            }
          }
        }
        .text-box {
          h1 {
            font-size: 4.5rem;
            font-weight: 400;
            margin-bottom: 30px;
            @media screen and (max-width: 768px) {
              color: #fff;
              font-size: 7vw;
            }
          }
          p {
            font-size: 1.7rem;
          }
        }
      }
    }
  }
}
</style>
