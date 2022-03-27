<template>
  <div class="footer-wrapper">
    <div class="footer-grid">
      <div class="box-content-top">
        <div class="region">
          <div class="img">
            <img
              src="https://www.playstation.com/etc.clientlibs/global_pdc/clientlibs/clientlib-base/resources/ps-bug.svg"
              alt=""
            />
          </div>
          <div class="region-content">
            <font-awesome-icon icon="fa-solid fa-globe" class="icon" />
            <span>Country / Region: United States</span>
          </div>
        </div>
        <div class="categories">
          <ul class="category-list" v-for="(item, index) in category" :key="index">
            <li v-for="(value, idx) in item.list" :key="idx">{{ value }}</li>
          </ul>
        </div>
      </div>
      <div class="box-content-bottom">
        <div class="sony">
          <div class="img">
            <img
              src="https://www.playstation.com/etc.clientlibs/global_pdc/clientlibs/clientlib-base/resources/sie.svg"
              alt=""
            />
          </div>
          <span>© 2022 Sony Interactive Entertainment LLC</span>
        </div>
        <div class="privacy">
          <img
            src="https://www.playstation.com/content/dam/global_pdc/en/external-resources/age-ratings/esrb/esrb.svg"
            alt=""
          />
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'FooterComponent',
  data() {
    return {
      category: [
        {
          list: [
            'Suppor',
            'Privacy policy',
            'Website terms of use',
            'PlayStation Studios',
            'Legal',
            'About SIE',
            'PlayStation and the environment',
          ],
        },
        {
          list: [
            'PSN terms of service',
            'PS Store cancellation policy',
            'Health warning',
            'About ratings',
            'About ratings',
            'Careers',
            'Developers',
            'Site map',
          ],
        },
        {
          list: ['Facebook', 'Twitter', 'Youtube', 'Instagram'],
        },
      ],
    };
  },
};
</script>

<style lang="scss" scoped>
.footer-wrapper {
  display: flex;
  justify-content: center;
  background: var(--dark-blue);
  padding: 64px 0;
  min-height: 456px;
  @media screen and (max-width: 760px) {
    padding-left: 20px;
  }
  .footer-grid {
    max-width: 1320px;
    width: 100%;
    display: flex;
    flex-direction: column;
    color: var(--white-color);
    .box-content-top {
      width: 100%;
      display: flex;
      justify-content: space-between;
      @media screen and (max-width: 760px) {
        flex-direction: column;
      }
      .categories {
        display: grid;
        grid-template-columns: 1fr 1fr 1fr;
        column-gap: 30px;
        @media screen and (max-width: 760px) {
          grid-template-columns: 1fr;
        }
        .category-list {
          list-style: none;
          li {
            font-size: 1.5rem;
            font-weight: 400;
            margin-bottom: 10px;
            cursor: pointer;
          }
          @media screen and (max-width: 760px) {
            margin-bottom: 30px;
          }
        }
      }
      .region {
        @media screen and (max-width: 760px) {
          margin-bottom: 30px;
        }
        .img {
          img {
            cursor: pointer;
            width: 96px;
            object-fit: contain;
          }
        }
        .region-content {
          display: flex;
          align-items: start;
          margin-top: 20px;
          .icon {
            margin-right: 10px;
            cursor: pointer;
            font-size: 2rem;
          }
          span {
            cursor: pointer;
            font-size: 1.4rem;
            font-weight: 400;
          }
        }
      }
    }
    .box-content-bottom {
      display: flex;
      justify-content: space-between;
      align-items: end;
      width: 100%;
      @media screen and (max-width: 760px) {
        flex-direction: column-reverse;
        align-items: start;
      }
      .sony {
        .img {
          margin-bottom: 10px;
          img {
            cursor: pointer;
            height: 48px;
            object-fit: contain;
          }
        }
        span {
          cursor: pointer;
          font-size: 1.5rem;
          font-weight: 400;
        }
      }
      .privacy {
        img {
          cursor: pointer;
          height: 60px;
          object-fit: contain;
        }
        @media screen and (max-width: 760px) {
          margin-bottom: 30px;
        }
      }
    }
  }
}
</style>
