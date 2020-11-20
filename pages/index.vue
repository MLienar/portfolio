<template>
  <div class="index">
    <FondTransition />
    <Splash />
    <Parots />
    <MangaBata />
    <SpeedLearning />
    <Diner />
  </div>
</template>

<script>
import Parots from '@/components/home-components/Parots'
import MangaBata from '@/components/home-components/MangaBata'
import Splash from '@/components/home-components/Splash'
import SpeedLearning from '@/components/home-components/SpeedLearning'
import Diner from '@/components/home-components/Diner'
import FondTransition from '@/components/FondTransition'


export default {
  name: 'Home',
  components: {
    Parots,
    MangaBata, 
    Splash,
    FondTransition
  },
  props: {
  },
  mounted: function() {
        this.slideTransition()
        // this.scrollMagicInit()
    },
  methods: {
      slideTransition: function() {
        const tl = new TimelineMax()
        tl.to('.fond-transition', 0.8, {width: "0", height:"100vh"})
      }
  },

  transition: {
    mode: 'out-in',
    css: false,
    leave (el, done) {
        const tl = new TimelineMax()
        
        tl.to('.home-case', 0.2, {opacity: "0", transform: "translate(10%, 0)" }, 0)
        tl.to('.hero-photo img', 0.5, {opacity: "0", transform: "scale(1.1) translateY(10%)"}, 0)
        tl.to('.fond-couleur', 0.5, {width: "100vw", height:"100vh", onComplete: done}, 0.2)
        
    }
  }
}
</script>

<style>
  .phone-photo {
      display:none;
  }

  @media screen and (max-width: 1100px) {
    img.laptop {
      right: 0 !important;
    }
  }
  @media screen and (max-width: 700px) {
    .fond-couleur {
      min-width: 100vw;
      z-index: 2;
      text-align: center;
    }
    .phone-photo {
    display: block !important;
    max-width: 50vw;
    max-height: 30vh;
    margin: 0 auto 5vh auto;
    }
    .home-case {
        text-align: center;
        width: 80vw !important;
    }
  }
</style>
