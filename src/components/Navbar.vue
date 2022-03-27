<template>
  <!-- eslint-disable max-len -->
  <!-- eslint-disable vuejs-accessibility/click-events-have-key-events -->
  <div class="nav-bar">
    <div class="nav-logo">
      <div class="sony-logo"></div>
    </div>
    <div id="nav-wrapper" class="nav-item-wrapper" ref="parentRef">
      <div class="wrapper">
        <div class="nav-mobile">
          <font-awesome-icon
            icon="fa-solid fa-bars"
            class="icon-bars active"
            @click="handleOpen"
            ref="openRef"
          />
          <font-awesome-icon
            icon="fa-solid fa-xmark"
            class="icon-close"
            @click="handleClose"
            ref="closeRef"
          />
        </div>
        <div class="nav-direct-wrapper">
          <router-link to="/ps4" class="nav-ps-logo">
            <svg
              class="ps-logo"
              width="50px"
              height="50px"
              version="1.1"
              xmlns="http://www.w3.org/2000/svg"
              xmlns:xlink="http://www.w3.org/1999/xlink"
              viewBox="0 0 50 50"
              data-di-res-id="b25db13e-fa034ecb"
              data-di-rand="1647826788490"
            >
              <g>
                <g>
                  <path
                    d="M5.8,32.1C4.3,33.1,4.8,35,8,35.9c3.3,1.1,6.9,1.4,10.4,0.8c0.2,0,0.4-0.1,0.5-0.1v-3.4l-3.4,1.1
       c-1.3,0.4-2.6,0.5-3.9,0.2c-1-0.3-0.8-0.9,0.4-1.4l6.9-2.4V27l-9.6,3.3C8.1,30.7,6.9,31.3,5.8,32.1z M29,17.1v9.7
       c4.1,2,7.3,0,7.3-5.2c0-5.3-1.9-7.7-7.4-9.6C26,11,23,10.1,20,9.5v28.9l7,2.1V16.2c0-1.1,0-1.9,0.8-1.6C28.9,14.9,29,16,29,17.1z
        M42,29.8c-2.9-1-6-1.4-9-1.1c-1.6,0.1-3.1,0.5-4.5,1l-0.3,0.1v3.9l6.5-2.4c1.3-0.4,2.6-0.5,3.9-0.2c1,0.3,0.8,0.9-0.4,1.4
       l-10,3.7V40L42,34.9c1-0.4,1.9-0.9,2.7-1.7C45.4,32.2,45.1,30.8,42,29.8z"
                    fill="#0070d1"
                  ></path>
                </g>
              </g>
            </svg>
          </router-link>
          <router-view />
          <div class="nav-wrap" ref="navWrapRef">
            <div class="nav-item-wrap" ref="navMobile">
              <div
                class="nav-direct-item"
                v-for="(item, index) in navItem"
                :key="index"
                @click="() => handleClick(index)"
              >
                <div class="item-text-wrap">
                  <div class="nav-img-mobile">
                    <img :src="require(`@/assets/images/nav-mobile/${navMobile[index]}`)" alt="" />
                  </div>
                  <span>{{ item.title }}</span>
                </div>
                <font-awesome-icon icon="fa-solid fa-angle-down" class="icon" />
              </div>
            </div>
          </div>
        </div>
        <div class="nav-sign-in-wrapper">
          <button>Sign In</button>
          <font-awesome-icon icon="fa-solid fa-magnifying-glass" class="icon" />
        </div>
      </div>
      <div :class="['expand-wrapper', isShow ? 'active' : '']">
        <div class="icon-control-close" @click="closeExpand">
          <font-awesome-icon icon="fa-solid fa-arrow-right" class="icon" />
        </div>
        <div id="list" :class="['list', isShow ? 'active' : '']" ref="listRef">
          <router-link
            :to="navItem[i].path"
            class="item"
            v-for="(n, i) in navItem[isClicked === -1 ? 0 : isClicked].list"
            :key="i"
            ref="itemRef"
          >
            <div class="img-contain">
              <img
                :src="
                  require(`@/assets/images/navbar/${
                    navItem[isClicked === -1 ? 0 : isClicked].img[i]
                  }`)
                "
                alt=""
              />
            </div>
            <div class="title">
              <span>{{ navItem[isClicked === -1 ? 0 : isClicked].list[i] }}</span>
            </div>
          </router-link>
          <router-view />
        </div>
        <div :class="['list-options', isShow ? 'active' : '']">
          <div
            class="option"
            v-for="(item, index) in navItem[isClicked === -1 ? 0 : isClicked].description"
            :key="index"
          >
            <font-awesome-icon icon="fa-solid fa-circle" class="icon" />
            <span>{{ item }}</span>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'NabarComponent',
  data() {
    return {
      navItem: [
        {
          title: 'Games',
          list: ['PS5', 'PS4', 'PS VR', 'PS Plus', 'PS Now', 'Buy Games'],
          img: ['ps5.png', 'ps4.png', 'psvr.png', 'psplus.png', 'psnow.png', 'store.png'],
          description: ['PlayStation Indies', 'PS4 games on PS5', 'Free to Play', 'Deals & offers'],
          path: '/ps4',
        },
        {
          title: 'Hardware',
          list: ['PS5', 'PS4', 'PS4 Pro', 'PS VR'],
          img: ['ps5.png', 'ps4.png', 'ps4pro.png', 'psvr.png'],
          description: [
            'DualSense wireless controller',
            'PULSE 3D wireless headset',
            'PS5 accessories',
            'PlayStation VR2',
            'PS4 accessories',
          ],
          path: '',
        },
        {
          title: 'Services',
          list: ['PS Plus', 'PS Now'],
          img: ['psplus.png', 'psnow.png'],
          description: ['PS5 entertainment', 'PS4 entertainment'],
          path: '',
        },
        {
          title: 'News',
          list: ['PS Blog', 'This Month on PlayStation'],
          img: ['psblog.png', 'calendar.png'],
          description: ['Competition Center', 'Accessibility'],
          path: '',
        },
        {
          title: 'Shop',
          list: ['Hardware and Disc', 'Digital Games and Services', 'Official Merchandise'],
          img: ['ps4pro.png', 'store.png', 'merchandise.png'],
          description: [
            'Buy PS5 games',
            'Buy PS4 games',
            'Buy PlayStation Plus',
            'Buy PS4',
            'Buy PS VR',
          ],
          path: '',
        },
        {
          title: 'Support',
          list: ['Support', 'PSN Status'],
          img: ['support.png', 'status.png'],
          description: [],
          path: '',
        },
      ],
      navMobile: ['img_1.png', 'img_2.png', 'img_6.png', 'img_3.png', 'img_4.png', 'img_5.png'],
      isClicked: -1,
      isShow: false,
    };
  },
  watch: {
    isShow(val) {
      if (val === true) {
        if (window.innerWidth <= 700) {
          document.querySelector('html').style.overflow = 'hidden';
        }
      } else {
        // eslint-disable-next-line no-lonely-if
        if (window.innerWidth <= 700) {
          document.querySelector('html').style.overflow = 'unset';
        }
      }
    },
  },
  methods: {
    handleClick(index) {
      if (index === this.isClicked && this.isShow) this.isShow = false;
      else if (index === this.isClicked && !this.isShow) this.isShow = true;
      else this.isShow = true;
      this.isClicked = index;
    },
    handleClickExpand(e) {
      if (!e.target.closest('#nav-wrapper')) this.isShow = false;
    },
    handleOpen() {
      this.$refs.navWrapRef.classList.add('active');
      this.$refs.navMobile.classList.add('active');
      this.$refs.openRef.classList.remove('active');
      this.$refs.closeRef.classList.add('active');
    },
    handleClose() {
      this.$refs.navWrapRef.classList.remove('active');
      this.$refs.navMobile.classList.remove('active');
      this.$refs.openRef.classList.add('active');
      this.$refs.closeRef.classList.remove('active');
    },
    closeExpand() {
      this.isShow = false;
    },
  },
};
</script>

<style lang="scss" scoped>
.fade-enter-active,
.fade-leave-active {
  transition: opacity 0.5s ease;
}

.fade-enter-from,
.fade-leave-to {
  opacity: 0;
}
.nav-bar {
  display: flex;
  flex-direction: column;
  .nav-logo {
    display: flex;
    align-items: center;
    justify-content: flex-end;
    background: var(--black-color);
    height: 36px;
    width: 100%;
    .sony-logo {
      margin: 0 10px;
      width: 75px;
      height: 100%;
      display: inline-block;
      background-image: url("https://www.playstation.com/etc.clientlibs/global_pdc/clientlibs/clientlibs-jetstream/resources/assets/fonts/sony_logo.svg");
      background-repeat: no-repeat;
      background-position: center;
    }
  }
  .nav-item-wrapper {
    position: relative;
    font-size: 1.2rem;
    font-weight: 500;
    display: flex;
    align-items: center;
    padding: 15px 20px;
    .wrapper {
      display: flex;
      width: 100%;
      align-items: center;
      justify-content: space-between;
      .nav-mobile {
        display: none;
      }
      @media screen and (max-width: 700px) {
        .nav-mobile {
          font-size: 2rem;
          cursor: pointer;
          position: relative;
          width: 22px;
          display: block;
          .icon-bars {
            display: none;
            &.active {
              display: block;
            }
          }
          .icon-close {
            position: absolute;
            left: 0;
            top: 0;
            font-size: 2.8rem;
            display: none;
            &.active {
              transform: translateY(-50%);
              display: block;
            }
          }
        }
      }
      .nav-direct-wrapper {
        display: flex;
        align-items: center;
        .nav-ps-logo {
          cursor: pointer;
          padding-right: 10px;
        }
        .nav-wrap {
          @media screen and (max-width: 700px) {
            position: fixed;
            overflow: hidden;
            display: flex;
            z-index: -1;
            top: 114px;
            left: 0;
            right: 0;
            bottom: 0;
            &.active {
              z-index: 99;
            }
          }
          .nav-item-wrap {
            display: flex;
            align-items: center;
            @media screen and (max-width: 700px) {
              flex-direction: column;
              display: block;
              width: 100%;
              background: var(--white-color);
              align-items: unset;
              opacity: 0;
              transition: transform 0.5s linear;
              transform: translateY(-100%);
              &.active {
                opacity: 1;
                transform: translateY(0);
              }
              .nav-direct-item {
                display: flex;
                align-items: center;
                justify-content: space-between;
              }
            }
            .nav-direct-item {
              padding-right: 10px;
              cursor: pointer;
              display: flex;
              align-items: center;
              padding: 10px 5px 10px 10px;
              &:hover,
              &:hover .icon {
                color: var(--main-color);
              }
              .item-text-wrap {
                display: flex;
                align-items: center;
                padding-right: 10px;
                .nav-img-mobile {
                  margin-right: 10px;
                  width: 26px;
                  height: 26px;
                  display: none;
                  img {
                    width: 100%;
                    height: 100%;
                    object-fit: contain;
                  }
                  @media screen and (max-width: 700px) {
                    display: block;
                  }
                }
              }
              .icon {
                padding-left: 2px;
                color: var(--light-grey);
                @media screen and (max-width: 700px) {
                  transform: rotateZ(-90deg);
                }
              }
            }
          }
        }
        @media screen and (max-width: 700px) {
          .nav-ps-logo {
            padding: 0;
            transform: translateX(50%);
          }
        }
      }
      .nav-sign-in-wrapper {
        button {
          color: var(--white-color);
          font-size: 1.4rem;
          padding: 5px 15px;
          font-weight: 600;
          background-color: var(--light-black);
          border: none;
          outline: none;
          border-radius: 20px;
          margin-right: 20px;
          cursor: pointer;
          &:hover {
            filter: brightness(1.4);
          }
          @media screen and (max-width: 700px) {
            margin: 0;
          }
        }
        .icon {
          cursor: pointer;
          font-size: 2rem;
          align-self: baseline;
          @media screen and (max-width: 700px) {
            display: none;
          }
        }
      }
    }
    .expand-wrapper {
      position: absolute;
      bottom: 0;
      left: 0;
      right: 0;
      transform: translateY(99%);
      transition: all 0.5s linear;
      height: 0;
      z-index: -1;
      pointer-events: none;
      background-color: var(--white-color);
      box-shadow: 0 5px 5px var(--light-text);
      overflow: hidden;
      @media screen and (max-width: 700px) {
        position: fixed;
        z-index: 100;
        top: 36px;
        left: 30%;
        right: 0;
        bottom: 0;
        transform: translate(100%, 0);
        overflow-y: scroll;
        box-shadow: 0 0px 10px var(--light-grey);
        &.active {
          height: fit-content !important;
          z-index: 99;
          transform: translate(0, 0);
          pointer-events: unset;
          .list {
            opacity: unset;
            background: var(--white-color);
          }
          .list-options {
            display: grid;
            grid-template-columns: repeat(2, 50%);
            justify-content: unset;
          }
        }
      }
      &.active {
        height: 220px;
        z-index: 99;
        pointer-events: unset;
      }
      .icon-control-close {
        display: none;
        @media screen and (max-width: 700px) {
          display: block;
          padding: 10px 20px;
          cursor: pointer;
        }
      }
      .list {
        display: grid;
        grid-template-columns: repeat(auto-fit, 150px);
        align-items: center;
        justify-content: center;
        padding: 10px 0 30px;
        border-bottom: 1px solid var(--light-grey);
        opacity: 0;
        animation: fadeOutNavItem 0.5s ease forwards;
        &.active {
          animation: fadeInNavItem 1s ease forwards;
        }
        .item {
          display: flex;
          flex-direction: column;
          align-items: center;
          padding: 10px;
          margin: 0 5px;
          transition: all 0.5s ease;
          cursor: pointer;
          height: 130px;
          &.anmation {
            animation: fadeOpacity 0.5s ease forwards;
          }
          &:hover {
            border-radius: 8px;
            box-shadow: 0 0 5px var(--light-black);
            transform: translate(-1px, -1px);
          }
          .img-contain {
            transition: all 0.4s linear;
            height: 60px;
            img {
              height: 50px;
              object-fit: contain;
            }
          }
          .title {
            text-align: center;
            height: 30px;
            margin-top: 10px;
            font-size: 1.5rem;
            font-weight: bold;
          }
        }
      }
      .list-options {
        display: flex;
        justify-content: center;
        align-items: center;
        padding: 20px 0;
        font-size: 1.4rem;
        animation: fadeOutNavItem 0.2s ease forwards;
        &.active {
          animation: fadeInNavItem 2.2s ease forwards;
        }
        .option {
          margin: 0 20px;
          display: flex;
          align-items: center;
          font-weight: bold;
          .icon {
            font-size: 0.7rem;
            color: var(--main-color);
            margin-right: 10px;
          }
        }
      }

      @keyframes fadeInNavItem {
        0% {
          opacity: 0;
        }
        100% {
          opacity: 1;
        }
      }
      @keyframes fadeOutNavItem {
        0% {
          opacity: 1;
        }
        100% {
          opacity: 0;
        }
      }
    }
  }
}
</style>
