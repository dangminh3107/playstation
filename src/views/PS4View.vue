<template>
  <div class="ps4-view">
    <Navbar />
    <BannerStaticV1 :dataArr="dataArr.banner1" />
    <ProductHardware :dataArr="dataArr.product" @isShowChange="show = $event" />
    <BannerClip :dataArr="dataArr.bannerVid" />
    <BannerSingleProduct :dataArr="dataArr.singleProduct" />
    <BannerPlay :dataArr="dataArr.bannerPlay1" />
    <BannerHits :dataArr="dataArr.bannerHits" :sizeWidth="sizeWidth" />
    <BannerVR :dataArr="dataArr.bannerVR" />
    <BannerPlus :dataArr="dataArr.bannerPlus" :sizeWidth="sizeWidth" />
    <BannerPlay :dataArr="dataArr.bannerPlay2" />
    <BannerHits :dataArr="dataArr.incredible" :sizeWidth="sizeWidth" />
    <Entertainment :dataArr="dataArr.entertainment" />
    <Connect :dataArr="dataArr.connectBlock" />
    <PS4Experience :dataArr="dataArr.experience" :sizeWidth="sizeWidth" />
    <Family :dataArr="dataArr.family" />
    <Section />
    <Footer />
  </div>
</template>

<script>
import Navbar from '../components/Navbar.vue';
import BannerStaticV1 from '../components/PS4View/BannerStaticV1.vue';
import ProductHardware from '../components/ProductHardware.vue';
import BannerClip from '../components/BannerClip.vue';
import BannerSingleProduct from '../components/BannerSingleProduct.vue';
import BannerPlay from '../components/PS4View/BannerPlay.vue';
import BannerHits from '../components/PS4View/BannerHits.vue';
import BannerVR from '../components/BannerVR.vue';
import BannerPlus from '../components/PS4View/BannerPlus.vue';
import Entertainment from '../components/PS4View/Entertainment.vue';
import Connect from '../components/PS4View/Connect.vue';
import PS4Experience from '../components/PS4View/PS4Experience.vue';
import Family from '../components/PS4View/Family.vue';
import Section from '../components/PS4View/Section.vue';
import Footer from '../components/Footer.vue';

export default {
  name: 'HomeView',
  components: {
    Navbar,
    BannerStaticV1,
    ProductHardware,
    BannerClip,
    BannerSingleProduct,
    BannerPlay,
    BannerHits,
    BannerVR,
    BannerPlus,
    Entertainment,
    Connect,
    PS4Experience,
    Family,
    Section,
    Footer,
  },
  created() {
    window.addEventListener('resize', this.handleResize);
  },
  destroyed() {
    window.removeEventListener('resize', this.handleResize);
  },
  data() {
    return {
      sizeWidth: 0,
      dataArr: {
        show: false,
        banner1: {
          image: 'img_1.jpg',
          logo: 'logo.png',
          text: ['Incredible games.', 'Non-stop entertainment.'],
        },
        product: {
          h1: 'Choose your PS4™ console',
          h2: 'Your choice of power. The same amazing games and entertainment.',
          list: [
            {
              image: 'img_1.jpg',
              name: 'PlayStation®4',
              overview: 'Incredible games live on PS4, with 1TB storage.',
              sub: 'Vertical stand sold separately',
            },
            {
              image: 'img_2.jpg',
              name: 'PlayStation®4 Pro',
              overview: '4K-gaming and entertainment with vibrant HDR1',
              sub: 'Vertical stand sold separately',
            },
          ],
        },
        bannerVid: {
          path: 'https://gmedia.playstation.com/is/content/SIEPDC/global_pdc/en/games/pdps/g/gh/ghost-of-tsushima/ghost-of-tsushima-video-hero-02-ps4-en-01may20.mp4',
          title: 'Discover PS4 games',
          overview:
            "Join Samurai warriors, hardened survivors and mighty gods in some of the most acclaimed titles ever made, including games created by PlayStation Studios that you can't play anywhere else.",
          btnContent: 'Discover PS4 games',
        },
        singleProduct: {
          h1: 'Incredible games & non-stop entertainment',
          h3: 'The PS4 console, delivering awesome gaming power, incredible entertainment and vibrant HDR technology1.',
          image: 'img_3.jpg',
          title: 'More ways to play',
          overview:
            'Store your games, apps, screenshots and videos with up to 1TB storage inside the PS4 console – slimmer and lighter than the original PS4 model and available in Jet Black and more colors.',
        },
        bannerVR: {
          header: 'PlayStation VR games',
          subHead:
            'Live the game in extraordinary new ways with PS4 and PlayStation VR. Simply connect the PS VR headset to your console and immerse yourself in breathtaking virtual-reality games, experiences and entertainment.',
          background: 'img_1.jpg',
          overlay: 'img_1_1.jpg',
          btn: 'Live the game with PS VR',
          colorHead: 'rgba(255,255,255,0.6)',
          colorBtn: '#21353e',
          colorText: '#00adfb',
        },
        bannerPlay1: {
          background: 'banner_3/img_1.jpg',
          colorBg: '#00439c',
          header: 'Play it on PlayStation',
          overview:
            'Build your way to a Victory Royale, win the World Series and lead your squad into battle. With some of the biggest and best games available on PS4 and millions of players worldwide, everyone’s here waiting for you.',
          btnContent: 'PS4 games on PS Store',
          colorBtn: '#000',
          bgBtn: '#fff',
          colorHover: '#fff',
        },
        bannerPlus: {
          background: 'ps4view/banner_4/img_2.jpg',
          backgroundMobile: 'ps4view/banner_4/img_3.jpg',
          textImg: 'ps4view/banner_4/img_1.jpg',
          headTitle: 'Take on the world with PlayStation Plus',
          overview:
            "Forge allegiances, settle scores and play with friends and rivals online in your favorite PS4 games' online modes with PlayStation Plus.",
          button: 'Join PS Plus',
          colorTextBtn: '#0699dc',
          colorBtn: '#27292e',
          color: '#fff',
          colorBoxContent: '#5f5e5d',
        },
        bannerPlay2: {
          background: 'banner_5/img_1.jpg',
          colorBg: '#00439c',
          header: 'Play online with PS4',
          overview:
            'Take your PS4 online with a PS Plus membership and join millions of players in competitive and cooperative games. Earn bragging rights from your friends in multiplayer matches in world famous sports franchises like FIFA and NBA 2K, back up your squad in Call of Duty or GTA Online or go free-to-play in the global phenomenon that is Fornite*.',
          btnContent: 'Online multiplayer with PS Plus',
          colorBtn: '#000',
          bgBtn: '#fff',
          colorHover: '#fff',
        },
        bannerHits: {
          title: 'PlayStation Hits',
          colorTitle: '#fff',
          background: 'banner_6/img_1.jpg',
          backgroundMobile: 'banner_6/img_1_1.jpg',
          overview:
            'Catch up with old friends at an affordable price. Some of the most iconic games of a generation are waiting for you in the PlayStation Hits range, including PlayStation exclusives, blockbuster hits and acclaimed games you may have missed.',
          colorOverview: '#fff',
          image: 'banner_6/img_2.jpg',
          contentBtn: 'Browse the range',
          colorBtn: '#352127',
          colorTextBtn: '#49a9e6',
        },
        incredible: {
          title: 'Incredible control',
          colorTitle: '#0072ce',
          background: 'banner_6/img_3.jpg',
          backgroundMobile: 'banner_6/img_3_1.jpg',
          overview:
            'An iconic design that fits perfectly in your hands, intuitive controls that keep you on top of your game and a vibrant array of colors to suit your style. However you like to play, the DUALSHOCK®4 wireless controller has you covered.',
          colorOverview: '#313131',
          contentBtn: 'See the full range',
          colorBtn: '#2d64e6',
          colorTextBtn: '#fff',
        },
        entertainment: {
          title: 'Access great entertainment',
          overview:
            "Discover the biggest and best movies, TV shows, video streaming services and all the world's music from your PS4 home screen4.",
          image: 'banner_7/img_1.jpg',
          contentBtn: 'Discover entertainment on PS4',
        },
        connectBlock: {
          title: 'Connect to your gaming world',
          subTitle: 'The freedom to play, share and socialise with millions of players worldwide.',
          remoteTitle: 'Remote Play',
          remoteSubTitle:
            'Stream games from your PS4 to any compatible iOS or Android device, PC, Mac, PlayStation Vita over your home WiFi network, and enjoy freedom from your TV.',
          remoteBtn: 'Learn more',
          remoteImg: 'banner_8/img_1.jpg',
          list: [
            {
              title: 'Share Play',
              image: 'banner_8/img_2.jpg',
              overview:
                'Let a friend play your games or join in multiplayer matches, even if they don’t own the game.',
            },
            {
              title: 'Stream your gameplay',
              image: 'banner_8/img_3.jpg',
              overview: 'Broadcast your adventures live to the world via Twitch and  YouTube.',
            },
            {
              title: 'Share in seconds',
              image: 'banner_8/img_4.jpg',
              overview:
                'Share screenshots and videos of your greatest moments on Twitter and YouTube.',
            },
            {
              title: 'Connect with friends',
              image: 'banner_8/img_5.jpg',
              overview:
                'Create parties, chat to friends or join gaming communities to find new players.',
            },
          ],
          btn: 'The PlayStation guide to sharing',
        },
        experience: {
          title: 'Great experiences that stay with you on PS4™ and PS5™',
          overview:
            'Discover some of the games, features and experiences that unite PS4 and PS5 consoles, and how the power of PlayStation®5 lets you push the boundaries of play.',
          image: 'banner_9/img_1.jpg',
          background: 'banner_9/img_2.jpg',
          backgroundMobile: 'banner_9/img_3.jpg',
          btn: 'Find out more',
        },
        family: {
          title: 'PS4 for the whole family',
          overview:
            'With versatile parental controls designed to give you peace of mind, plus a whole universe of games suitable for everyone, PS4 is suitable for the entire family.',
          list: [
            {
              image: 'banner_10/img_1.jpg',
              title: 'Parental controls on PS4',
              overview:
                'Parental controls on PS4 let you tailor what each individual child family member can access on their console, and how long they can play each day.',
              btn: 'Full details',
            },
            {
              image: 'banner_10/img_2.jpg',
              title: 'A parent’s guide to PlayStation',
              overview:
                "Learn more about what we do to keep young players as safe as possible – and what you can do to make sure they're playing in ways that are suitable for their age group.",
              btn: 'Find out more',
            },
          ],
          new: {
            image: 'banner_10/img_3.jpg',
            title: 'New to PS4?',
            overview:
              'Find everything you need to know to make the most of your PS4 in our new user guide.',
            btn: 'PS4 new user guide',
          },
        },
      },
    };
  },
  methods: {
    handleResize() {
      this.sizeWidth = window.innerWidth;
    },
  },
};
</script>

<style lang="scss" scoped></style>
