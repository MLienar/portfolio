<template>
    <div class="hero-photo">
        <img :src="require(`~/assets/${mockup}.png`)" :alt="alt" :class="classes">
    </div>
</template>

<script>
export default {
    name: 'HeroPhoto',
    props: ['mockup', 'alt', 'classes'],
    data() {
        return {

        }
    }
}
</script>

<style lang="scss">
.case-container {
    .hero-photo {
        width: 35vw;
        height: 100%;
        margin: 0;
        display: flex;
        align-items: center;
        top: 0;
        left: 0;
        animation-name: zoomin; 
        img {
            z-index:2;
            position: relative;
        }

        img.laptop {
            height: 15vw;
            min-height: 200px;
        }
        img.laptop.right {
            right: -15vw;
        }
        img.laptop.left {
            left: -15vw;
        }

        img.phone {
            height: 20vw;
            min-height: 350px;
        }
        img.phone.right {
            right: -15vw;
        }
        img.phone.left {
            left: -5vw;
        }
    }
}

.case-page {
    .hero-photo {
    position: relative;
    top: 0;
    width: 100vw;
    margin-top: 10vh;
    z-index: 2;
    display:flex;
    justify-content: center;
        img.laptop-case {
        width: 45vw;
        min-width: 300px;
        }
        img.phone-case {
        margin-top: 5vh;
        width: 10vw;
        min-width: 150px;
        }
    }
}

// Animations
@keyframes zoomin {
  from {
        width: 35vw;
        height: 100%;
  }
  50% {
        width: 100vw;
        height: 100%;
  }

  to {
    margin-left: 0%;
    width: 100%;
  }
}



</style>