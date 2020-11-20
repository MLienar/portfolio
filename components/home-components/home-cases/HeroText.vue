<template>
        <div class="fond-couleur">   
                <slot></slot>
        </div>
</template>

<script>
export default {
    name: 'HeroText',
    data() {
        return {

        }
    },

}
</script>

<style lang="scss">
    // Home Page
    .case-container {
        .fond-couleur {
            height: 100%;
            width: 65vw;
            display: flex;
            justify-content: center;
            align-items: center;
            text-align: left; 
            position: absolute;  
            overflow: hidden;          
            .home-case {
                width: 40%;
                color: white;
                @media screen and (max-width: 1400px) {
                    width: 60%;
                }
                h2 {
                    text-transform: uppercase;
                }
                p {
                    margin: 5vh 0;
                }
                a {
                    color: white;
                    text-decoration: none;
                    font-size: 3vh;
                    font-weight: 600;
                    padding-bottom: 1vh;
                    border-bottom: 0.5vh solid white;
                }
            }
        }
    }
    .right .fond-couleur {
        top: 0;
        right: 0;
        .hero-text {
        margin-left: 5vh;
        }
    }
    .left .fond-couleur {
        top: 0;
        left: 0;
        .hero-text {
        margin-left: 5vh;
        }
    }

    // Case page 
    .case-page {
        .fond-couleur {
            position: absolute;
            top: 0;
            height: 25vw;
            min-height: 250px;
            width: 100%;
            clip-path: polygon(0 0, 100% 0, 100% 100%, 0 67%);
        }
    }
</style>