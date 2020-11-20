<template>
    <div class="speed-learning">
        <div class="case-container right">
            <HeroPhoto :mockup="mockup" :alt="mockupalt" :classes="mockupclass" />
            <HeroText>
                <div class="home-case">
                    <img :src="require(`~/assets/${mockup}.png`)" :alt="alt" class="phone-photo">
                    <h2 class="title">Speed Learning</h2>
                    <p class="text">Speed Learning est un site dynamique développé et designé from scratch, puis intégré sur ModX, CMS Open-Source, pour permettre une mise à jour facile et fréquente du contenu.</p>
                    <nuxt-link to="/cases/speedlearning" class="cta">En savoir plus</nuxt-link>
                </div>  
            </HeroText>  
        </div>
    </div>
</template>

<script>
import HeroPhoto from '@/components/home-components/home-cases/HeroPhoto'
import HeroText from '@/components/home-components/home-cases/HeroText'

export default {
    name: 'Algofi',
    components: {
        HeroPhoto,
        HeroText
    },
    data(){
        return {
            mockup: 'algofi',
            mockupalt: "site web dédié aux formations",
            mockupclass: 'right laptop' 
        }
    },
    mounted: function() {
        this.startAnimations()
    },
    methods: {
        startAnimations: function () {

            const tl = new TimelineMax({onUpdate:updatePercentage})

            tl.from('.speed-learning .fond-couleur', 1, {width: "100vw", height:"100vh"}, 0)
            tl.from('.speed-learning .laptop', 0.5, {opacity: 0, transform: "scale(1.1)"}, 0.5)
            tl.from('.speed-learning .phone-photo', 0.5, {opacity: 0, transform: "scale(1.1)"}, 0.5)
            tl.from('.speed-learning .title', 0.5, {opacity: 0, transform: "translate(10%, 0)"}, 1)
            tl.from('.speed-learning .text', 0.5, {opacity: 0, transform: "translate(-10%, 0)"}, 1.2)
            tl.from('.speed-learning .cta', 0.5, {opacity: 0, transform: "translate(10%, 0)"}, 1.5)

            const scene = this.$scrollmagic.scene({
                triggerElement:'.speed-learning',
                triggerHook: 0,
                duration: '2000'
            })
            
            .setPin('.speed-learning')
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
    .speed-learning {
        overflow: hidden;
        .case-container {
            height: 100vh;
            display: flex;
            align-items: center;
            position: relative;
            overflow: hidden;
        }

        .fond-couleur {
            background: var(--gris);
        }
        .hero-photo {
        background: url(~assets/formation-it-finance.jpg);
        background-size: cover;
        background-position: bottom ;
        background-repeat: no-repeat;
        }

    }

</style>