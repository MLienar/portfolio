<template>
  <div class="case-page">
    <FondTransition />
    <HeroText />
    <HeroPhoto :mockup="mockup" :alt="mockupalt" :classes="classes"/>
    <h1 class="case-title">Speed Learning</h1>
    <p class="case-intro">Lorem ipsum dolor sit amet, consectetur adipiscing elit. Suspendisse malesuada purus eros, ac suscipit tortor semper ac. In posuere nec eros nec porta. Pellentesque vel justo in nisi elementum volutpat quis sit amet ipsum. Mauris quis lobortis sapien. Nam molestie magna urna, non egestas libero ornare ultricies. Pellentesque vitae</p>
    <BriefClient :mockup="mockupbrief" :alt="briefalt">Lorem ipsum dolor sit amet, consectetur adipiscing elit. Suspendisse malesuada purus eros, ac suscipit tortor semper ac. In posuere nec eros nec porta. Pellentesque vel justo in nisi elementum volutpat quis sit amet ipsum. Mauris quis lobortis sapien. Nam molestie magna urna, non egestas libero ornare ultricies. Pellentesque vitae</BriefClient>
    
    <div class="bloc-details">
      <div class="details enjeux">
        <div class="details-text">
          <h2>Contraintes<br>et enjeux</h2>
          <p>Lorem ipsum dolor sit amet, consectetur adipiscing elit. Suspendisse malesuada purus eros, ac suscipit tortor semper ac. In posuere nec eros nec porta. Pellentesque vel justo in nisi elementum volutpat quis sit amet ipsum. Mauris quis lobortis sapien. Nam molestie magna urna, non egestas libero ornare ultricies. Pellentesque vitae</p>
        </div>
      </div>

      <div class="details reponses">
        <div class="details-text">
          <h2>Solutions<br>proposées</h2>
          <p>Lorem ipsum dolor sit amet, consectetur adipiscing elit. Suspendisse malesuada purus eros, ac suscipit tortor semper ac. In posuere nec eros nec porta. Pellentesque vel justo in nisi elementum volutpat quis sit amet ipsum. Mauris quis lobortis sapien. Nam molestie magna urna, non egestas libero ornare ultricies. Pellentesque vitae</p>
        </div>
      </div>
      </div>

    <h2 class="technos">Technos</h2>
    <div class="bloc-technos">
      <Technos :techno="techno1">HTML</Technos>
      <Technos :techno="techno2">CSS</Technos>
      <Technos :techno="techno3">JS</Technos>
    </div>
  </div>
</template>

<script>
import HeroPhoto from '@/components/home-components/home-cases/HeroPhoto'
import HeroText from '@/components/home-components/home-cases/HeroText'
import FondTransition from '@/components/FondTransition'
import BriefClient from '@/components/case-components/BriefClient'
import Technos from '@/components/case-components/Technos'

export default {
  components: {
        HeroPhoto,
        HeroText,
        FondTransition,
        BriefClient, 
        Technos
  },
  data(){
    return {
        mockup: 'algofi',
        mockupalt: "site web des speed learning",
        classes: 'laptop-case',
        mockupbrief: 'algofi',
        briefalt: "site web de l'écurie algofi",
        techno1: "html",
        techno2: "css",
        techno3: "js",
    }
  },

  mounted: function() {
        this.startAnimations()
    },
    methods: {
        startAnimations: function () {
            const tl = new TimelineMax()
            tl.from('.fond-couleur', 0.5, {width: "100vw", height:"100vh", clipPath:"polygon(0 0, 100% 0, 100% 100%, 0 100%)"}, 0)
            tl.from('.hero-photo', 0.5, {opacity: 0, transform: "scale(1.1) translateY(-30%)"}, 0)
            tl.from('.case-title', 0.5, {opacity: 0, transform: "translateY(-10%)"}, 0.4)
            tl.from('.case-intro', 0.5, {opacity: 0, transform: "translateY(-10%)"}, 0.6)
        },
        changeTransitionBackround() {
           
        }
    },
    transition: {
    mode: 'out-in',
    css: false,
    

    leave (el, done) {
        const tl = new TimelineMax()
        tl.to('.fond-transition', 0.5, {width: "100vw", height:"100vh", clipPath:"polygon(0 0, 100% 0, 100% 100%, 0 100%)", onComplete: done}, 0.2)        
    }
  }
}   
</script>

<style lang="scss" scoped>
    .case-page {
        overflow: hidden;
        .fond-couleur {
          background: var(--gris);
        }
        .case-title {
          margin: 10vh auto 5vh auto;
          color: var(--noir);
          text-transform: uppercase;
          text-align: center;
          max-width: 90vw;
        }
        .case-intro {
          width: 40vw;
          min-width: 300px;
          text-align: center;
          margin: auto;
        }
        .technos {
            text-align: center;
            text-transform: uppercase;
            margin-top: 5vh;
          }
        .bloc-technos {
          display: flex;
          flex-flow: row nowrap;
          justify-content: center;
          align-items: center;
        
        }
    }
    .bloc-details {
      width: 100vw;
      display: flex;
      flex-flow: row nowrap;
      margin: 10vw 0;
      .details {
        width: 100%;
        padding: 7vw;
        display: flex;
        justify-content: center;
        align-items: center;
        h2 {
          text-transform: uppercase;
          margin-bottom: 5vh;
        }
        p {
          max-width: 550px;
        }
      }
      .enjeux {
        background: #F1F7F1;  
      }
      .reponses {
          background: var(--gris);
          color: white;
        }
    }

    @media screen and (max-width: 800px) {
      .case-intro {
        max-width: 90% !important;
      }

      .bloc-details{
        flex-flow: column nowrap;
      }

      .bloc-technos {
        flex-flow: column nowrap !important;
      }

      .details {
        padding: 15vh 7vh !important;
      }
      .technos {
        margin: 5vh auto;
      }
    }
</style>