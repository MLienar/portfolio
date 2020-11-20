<template>
    <div class="mangabata">
        <div class="case-container left">
            <HeroPhoto :mockup="mockup" :alt="mockupalt" :classes="mockupclass" />
            <HeroText>
                <div class="home-case">
                    <img :src="require(`~/assets/${mockup}.png`)" :alt="alt" class="phone-photo">
                    <h2 class="title">MangaBata</h2>
                    <p class="text" id="mangabata">Mangabata est une concept app designée dans le cadre d'un projet personnel. L'idée était d'imaginer une application permettant aux lecteurs de manga de se préter les tomes qui manquaient à leur collection.</p>
                    <nuxt-link to="/cases/mangabata" class="cta" >En savoir plus</nuxt-link>
                </div>
            </HeroText>
        </div>
    </div>
</template>

<script>
import HeroPhoto from '@/components/home-components/home-cases/HeroPhoto'
import HeroText from '@/components/home-components/home-cases/HeroText'

export default {
    name: 'Mangabata',
    components: {
        HeroPhoto,
        HeroText
    },
    data(){
        return {
            mockup: 'mangabata',
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

            tl.from('.mangabata .fond-couleur', 1, {width: "100vw", height:"100vh"}, 0)
            tl.from('.mangabata .phone', 0.5, {opacity: 0, transform: "scale(1.1)"}, 0.5)
            tl.from('.mangabata .phone-photo', 0.5, {opacity: 0, transform: "scale(1.1)"}, 0.5)
            tl.from('.mangabata .title', 0.5, {opacity: 0, transform: "translate(10%, 0)"}, 1)
            tl.from('.mangabata .text', 0.5, {opacity: 0, transform: "translate(-10%, 0)"}, 1.2)
            tl.from('.mangabata .cta', 0.5, {opacity: 0, transform: "translate(10%, 0)"}, 1.5)

            const scene = this.$scrollmagic.scene({
                triggerElement:'.mangabata',
                triggerHook: 0,
                duration: '2000'
            })
            
            .setPin('.mangabata')
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
    .mangabata {
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
            background: var(--orange);
        }
        .hero-photo {
        background: url(~assets/manga-fond.png);
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