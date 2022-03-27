<template>
  <div class="banner-video">
    <div class="video-wrapper">
      <video class="video" autoplay loop muted>
        <source :src="dataArr.path" type="video/mp4" />
      </video>
    </div>
    <div class="content-wrapper">
      <div class="content-overlay">
        <h1>{{ dataArr.title }}</h1>
        <p>{{ dataArr.overview }}</p>
        <button>{{ dataArr.btnContent }}</button>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'BannerClipComponent',
  props: ['dataArr'],
  data() {
    return {};
  },
};
</script>

<style lang="scss" scoped>
.banner-video {
  width: 100%;
  position: relative;
  .video-wrapper {
    position: relative;
    height: fit-content;
    max-height: 724px;
    overflow: hidden;
    &:after {
      content: "";
      position: absolute;
      height: 100%;
      top: 0;
      left: 0;
      width: 100%;
      background: linear-gradient(to right, var(--light-text) 0%, transparent 50%);
    }
    .video {
      margin-left: -3px;
      width: 101%;
      @media screen and (max-width: 768px) {
        margin-bottom: -5px;
      }
    }
  }
  .content-wrapper {
    @media screen and (max-width: 768px) {
      background: var(--main-color);
      padding: 40px 20px;
    }
    .content-overlay {
      color: var(--white-color);
      position: absolute;
      width: 40%;
      left: 8%;
      display: flex;
      flex-direction: column;
      align-items: start;
      background-color: rgba(31, 31, 31, 0.6);
      padding: 24px;
      bottom: 25%;
      @media screen and (max-width: 860px) and (min-width: 769px) {
        bottom: 15%;
      }
      @media screen and (max-width: 768px) {
        position: unset;
        width: 100%;
      }
      h1 {
        font-size: 3rem;
        line-height: 3rem;
        font-weight: 400;
      }
      p {
        font-size: 1.6rem;
        line-height: 2.5rem;
        padding: 20px 0;
      }
      button {
        font-size: 1.5rem;
        line-height: 1.5rem;
        font-weight: bold;
        padding: 10px 20px 12px;
        margin-left: 4px;
        border: none;
        border-radius: 20px;
        background-color: #2d64e6;
        color: var(--white-color);
        &:hover {
          outline: 3px solid #2d64e6;
          outline-offset: 3px;
        }
      }
    }
  }
}
</style>
