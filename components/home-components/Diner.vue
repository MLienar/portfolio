<template>
    <div class="diner">
        <div class="case-container left">
            <HeroPhoto :mockup="mockup" :alt="mockupalt" :classes="mockupclass" />
            <HeroText>
                <div class="home-case">
                    <img :src="require(`~/assets/${mockup}.png`)" :alt="alt" class="phone-photo">
                    <h2 class="title">diner <br></h2>
                    <p class="text" id="diner">Diner est un projet en cours dont l'objectif est d'être une interface de commande en ligne pour les restaurateurs. Pensé pour proposer une alternative aux leaders du marché, le projet verra bientôt jour. </p>
                    <nuxt-link to="/cases/diner" class="cta" >En savoir plus</nuxt-link>
                </div>
            </HeroText>
        </div>
    </div>
</template>

<script>
import HeroPhoto from '@/components/home-components/home-cases/HeroPhoto'
import HeroText from '@/components/home-components/home-cases/HeroText'

export default {
    name: 'Diner',
    components: {
        HeroPhoto,
        HeroText
    },
    data(){
        return {
            mockup: 'diner',
            mockupalt: "site web de l'écurie des parots",
            mockupclass: 'left phone' 
        }
    },
    mounted: function() {
        this.startAnimations()
    },
    methods: {
        startAnimations: function () {

            const tl = new TimelineMax({onUpdate:updatePercentage})

            tl.from('.diner .fond-couleur', 1, {width: "100vw", height:"100vh"}, 0)
            tl.from('.diner .phone', 0.5, {opacity: 0, transform: "scale(1.1)"}, 0.5)
            tl.from('.diner .phone-photo', 0.5, {opacity: 0, transform: "scale(1.1)"}, 0.5)
            tl.from('.diner .title', 0.5, {opacity: 0, transform: "translate(10%, 0)"}, 1)
            tl.from('.diner .text', 0.5, {opacity: 0, transform: "translate(-10%, 0)"}, 1.2)
            tl.from('.diner .cta', 0.5, {opacity: 0, transform: "translate(10%, 0)"}, 1.5)

            const scene = this.$scrollmagic.scene({
                triggerElement:'.diner',
                triggerHook: 0,
                duration: '2000'
            })
            
            .setPin('.diner')
            .setTween(tl)

            this.$scrollmagic.addScene(scene)

            function updatePercentage() {
                tl.progress()
            }
        },
    }
}
</script>

<style lang="scss">
    .diner {
        .case-container {
            height: 100vh;
            display: flex;
            align-items: center;
            position: relative;
            overflow: hidden;
        }
        
        .left {
            flex-flow: row-reverse nowrap;
        }

        .fond-couleur {
            background: var(--red);
        }
        .hero-photo {
        background: url(~assets/diner-back.jpg);
        background-size: cover;
        background-position: center;
        background-repeat: no-repeat;
        }
        .move-up {
        transition: all 0.8s ease-in-out;
        transform: translateY(-100vw);    
        }
    }
</style>