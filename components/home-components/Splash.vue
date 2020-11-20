<template>
  <div class="splash">
    <div class="splash-text">
        <h1 class="name">Mathéo Lienard<br>
        <span class="job">Front-End Developer</span></h1>
        <ul class="porfolio-links">
            <a href="#" v-scroll-to="{ element: '#parots', duration: 3000, offset: 2000 }"><div class="link"><div class="trait"></div><li class="splash-link">mes projets</li></div></a>
            <a href="#"><div class="link"><div class="trait"></div><li class="splash-link">mes compétences</li></div></a>
            <a href="mailto:matheolienardpro@gmail.com" target="_blank"><div class="link"><div class="trait"></div><li class="splash-link">me contacter</li></div></a>
        </ul>
    </div>
    <div class="splash-img">
        <div class="beigefadeup"></div>
        <div class="slide-background"></div>
        <div class="beigefadedown"></div>
    </div>
    
  </div>
</template>

<script>
export default {
    mounted: function() {
            this.splashAnimations()
        },
    methods: {
        splashAnimations: function () {
            const tl = new TimelineMax()
            tl.from('.name', 0.5, {opacity: 0, transform: "translateY(-30%)"}, 1)
            tl.from('.job', 0.5, {opacity: 0, transform: "translateY(-20%)"}, 1.5)
            tl.from('.link', 0.5, {opacity: 0, transform: "translateY(-10%)", stagger: 0.4}, 1.8)
            tl.from('.splash-img', 0.5, {opacity: 0, transform: "translateY(-20%) scale(1.1)"}, 1.8)
        }, 

        
    }
}
</script>

<style lang="scss">
    .splash {
        height: 100vh;
        width: 100vw;
        background: var(--lightbeige);
        display: flex;
        justify-content: space-evenly;
        align-items: center;
        
        .splash-text {
            color: white;
            width: 40vw;
            .name {
                text-transform: uppercase;
                font-weight: 700;
                margin-bottom: 5vh;
                .job {
                    -webkit-text-stroke: 1.5px white;
                    color: rgba(0 0 0 / 0);
                }
            }       
            ul {
                display: flex;
                flex-flow: column nowrap;
                a {
                    text-decoration: none;
                    color: white;
                    font-size: 3.2vh;
                    &:hover {
                        color: var(--brown);
                        transition: all 0.2s ease-in-out;
                        
                        .trait {
                            background: var(--brown);
                            width: 3vw;
                            transition: all 0.2s ease-in-out;
                        }
                    }
                    .trait {
                        width: 1.8vw;
                        height: .3vh;
                        background: white;
                        margin-right: 2vw;
                    }
                    .link {
                        display: flex; 
                        flex-flow: row nowrap;
                        align-items: center;
                        li {
                            list-style: none;
                        }
                    }   
                }
            }
        }
        .splash-img {
            position: relative;
            height: 80vh;
            width: 20vw;
            overflow: hidden;
            .beigefadeup {
                background: rgb(240,220,202);
                background: linear-gradient(180deg, rgba(240,220,202,1) 0%, rgba(240,220,202,1) 51%, rgba(240,220,202,0) 100%);
                position: absolute;
                top: -5px;
                left: -5px;
                width: 110%;
                height: 10%;
                z-index: 2;
            }
            .beigefadedown {
                background: rgb(240,220,202);
                background: linear-gradient(0deg, rgba(240,220,202,1) 0%, rgba(240,220,202,1) 50%, rgba(240,220,202,0) 100%);
                position: absolute;
                bottom: -5px;
                left: -5px;
                width: 110%;
                height: 10%;
                z-index: 2;
            }
            .slide-background {
                position: absolute;
                top: 0;
                left: 0;
                width: 100%;
                height: 5377px;
                background: url(~assets/splash-photo.jpg);
                background-size: contain;
                background-repeat: no-repeat; 
                background-position: bottom 70vh;
                animation: slide 40s linear infinite;
                @keyframes slide {
                    0%{
                        transform: translate3d(0, 0, 0);
                    }
                    100% {
                        transform: translate3d(0, -5377px, 0);
                    }
                }
            }
        }
    }

    // Media Queries

    @media screen and (max-width: 700px) {
        .splash-img {
            display: none !important;
        }
        .splash-text {
            width: 90vw !important;
        }
    }

</style>