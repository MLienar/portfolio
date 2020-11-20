<template>
    <div class="parots" id="parots">
        <div class="case-container right">
            <HeroPhoto :mockup="mockup" :alt="mockupalt" :classes="mockupclass" />
            <HeroText>
                <div class="home-case">
                    <img :src="require(`~/assets/${mockup}.png`)" :alt="alt" class="phone-photo">
                    <h2 class="title">Les écuries <br>des parots</h2>
                    <p class="text">Ecuries de propriétaires situées à Tallard, les écuries des Parots souhaitaient une refonte complète de leur site vitrine statique. Développée et designée from scratch, la solution proposée pose les bases d'une nouvelle identité pour les écuries, à la fois moderne et aventureuse. </p>
                    <nuxt-link to="/cases/parots" class="cta">En savoir plus</nuxt-link>
                </div>  
            </HeroText>  
        </div>
    </div>
    
</template>

<script>
import HeroPhoto from '@/components/home-components/home-cases/HeroPhoto'
import HeroText from '@/components/home-components/home-cases/HeroText'
import { gsap } from 'gsap'

export default {
    name: 'Parots',
    components: {
        HeroPhoto,
        HeroText
    },
    data(){
        return {
            mockup: 'parots',
            mockupalt: "site web de l'écurie des parots",
            mockupclass: 'right laptop' 
        }
    },
    mounted: function() {
        this.startAnimations()
    },

    methods: {
        startAnimations: function () {
            const tl = new TimelineMax()
            tl.from('.parots .fond-couleur', 1, {width: "100vw", height:"100vh"}, 0)
            tl.from('.parots .laptop', 0.5, {opacity: 0, transform: "scale(1.1)"}, 0.5)
            tl.from('.parots .phone-photo', 0.5, {opacity: 0, transform: "scale(1.1)"}, 0.5)
            tl.from('.parots .title', 0.5, {opacity: 0, transform: "translate(-10%, 0)"}, 0.8)
            tl.from('.parots .text', 0.5, {opacity: 0, transform: "translate(10%, 0)"}, 1.2)
            tl.from('.parots .cta', 0.5, {opacity: 0, transform: "translate(-10%, 0)"}, 1.7)
        

            const scene = this.$scrollmagic.scene({
                triggerElement:'.parots',
                triggerHook: 0,
                duration: '2000'
            })
            
            .setPin('.parots')
            .setTween(tl)

            this.$scrollmagic.addScene(scene)
            }
        }
}


</script>

<style lang="scss">
    .parots {
        overflow: hidden;
        .case-container {
            height: 100vh;
            display: flex;
            align-items: center;
            position: relative;
            overflow: hidden;
        }

        .fond-couleur {
            background: var(--vert);
        }
        .hero-photo {
        background: url(~assets/ecurie-montagne.jpg);
        background-size: cover;
        background-position: center;
        background-repeat: no-repeat;
        }

    }


    
</style>