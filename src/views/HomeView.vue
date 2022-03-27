<template>
  <div id="home-view">
    <Navbar />
    <BannerGame
      :indexClicked="indexCarousel"
      :listItem="bannerGame1"
      @sizeOfWindow="sizeWindow = $event"
    />
    <CarouselGame @indexWasClicked="indexCarousel = $event" />
    <BannerConsole :indexClicked="indexCarouselConsole" />
    <CarouselConsole @indexConsole="indexCarouselConsole = $event" />
    <Experience />
    <BannerGame :indexClicked="indexCarousel2" :listItem="bannerGame2" />
    <ListGame />
    <Explore />
    <BannerGameV2 :sizeWindow="sizeWindow" :objData="objData[0]" />
    <Sale />
    <BannerGameV2 :sizeWindow="sizeWindow" :objData="objData[1]" />
    <Socials />
    <Footer />
  </div>
</template>

<script>
import Navbar from '../components/Navbar.vue';
import BannerGame from '../components/BannerGame.vue';
import BannerConsole from '../components/BannerConsole.vue';
import CarouselGame from '../components/CarouselGame.vue';
import CarouselConsole from '../components/CarouselConsole.vue';
import Experience from '../components/Experience.vue';
import ListGame from '../components/ListGame.vue';
import Explore from '../components/Explore.vue';
import BannerGameV2 from '../components/BannerGameV2.vue';
import Sale from '../components/Sale.vue';
import Socials from '../components/Socials.vue';
import Footer from '../components/Footer.vue';

export default {
  name: 'HomeView',
  components: {
    Navbar,
    BannerGame,
    BannerConsole,
    CarouselGame,
    CarouselConsole,
    Experience,
    ListGame,
    Explore,
    BannerGameV2,
    Sale,
    Socials,
    Footer,
  },
  data() {
    return {
      indexCarousel: 0,
      indexCarousel2: 0,
      indexCarouselConsole: 0,
      sizeWindow: 0,
      bannerGame1: [
        {
          image: 'banner_1/img_1.jpg',
          imageMobile: 'banner_1/img_1_800.jpg',
          imageTitle: 'banner_1/img_1_1.jpg',
          title: 'Live the unwritten',
          overview:
            'Hogwarts Legacy is an immersive, open-world action RPG set in the world first introduced in the Harry Potter books.',
          color: '#fff',
        },
        {
          image: 'banner_1/img_2.jpg',
          imageMobile: 'banner_1/img_2_800.jpg',
          imageTitle: 'banner_1/img_2_1.jpg',
          title: 'Available now on PS5',
          overview:
            'Get GTA Online free, exclusively on PS5 until June 14, 2022.',
          color: '#fff',
        },
        {
          image: 'banner_1/img_3.jpg',
          imageMobile: 'banner_1/img_3_800.jpg',
          imageTitle: 'banner_1/img_3_1.jpg',
          title: "It's time to kill Chaos",
          overview:
            'Experience a bold new vision for the Final Fantasy series in this intense action RPG from Square Enix and Team Ninja, out now on PS4 & PS5.',
          color: '#1f1f1f',
        },
        {
          image: 'banner_1/img_4.jpg',
          imageMobile: 'banner_1/img_4_800.jpg',
          imageTitle: 'banner_1/img_4_1.jpg',
          title: 'Find your line',
          overview:
            'Gran Turismo 7 builds on generations of racing sim experience to bring you the best features from the history of the franchise.',
          color: '#fff',
        },
        {
          image: 'banner_1/img_5.jpg',
          imageMobile: 'banner_1/img_5_800.jpg',
          imageTitle: 'banner_1/img_5_1.jpg',
          title: 'Break the cycle',
          overview:
            'Return to Atropos with this huge new free update, including full co-op play and the fearsome new Tower of Sisyphus area, out now on PS5',
          color: '#fff',
        },
      ],
      bannerGame2: [
        {
          image: 'banner_3/img_23.jpg',
          imageMobile: 'banner_3/img_23_800.jpg',
          imageTitle: 'banner_3/img_24.jpg',
          title: 'Own The Show™',
          overview:
            'Every pitch. Every hit. Every win. Make your mark and Own The Show in MLB® The Show™ 22.',
          color: '#fff',
        },
      ],
      objData: [
        {
          background: 'banner_4/background.jpg',
          overlay: 'banner_4/img_52.jpg',
          textImg: 'banner_4/img_53.jpg',
          overview:
            'Enhance your PlayStation experience with access to online multiplayer, monthly games, exclusive discounts and more.',
          button: 'Explore PlayStation Plus',
          color: '',
          colorBgMobile: '#C1BDBC',
        },
        {
          background: 'banner_5/background.jpg',
          overlay: 'banner_5/img_54.jpg',
          textImg: 'banner_5/img_55.jpg',
          overview:
            'Gain instant access to a huge collection of more than 800 PS4, PS3 and PS2 games on PS4 or Windows PC, with new games added every month.',
          button: 'Explore PlayStation Now',
          color: '#fff',
          colorTextBtn: '#000',
          colorBtn: '#fff',
          outlineColor: '#fff',
          colorBgMobile: '#0a1432',
        },
      ],
    };
  },
};
</script>

<style lang="scss"></style>
