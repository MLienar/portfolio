<template>
  <div class="techno">
      <img :src="require(`~/assets/${techno}.svg`)" alt="logo du langage de programmation">
      <h3><slot></slot></h3>
  </div>
</template>

<script>
export default {
    name: 'Technos',
    props: ['techno']
}
</script>

<style lang="scss">
    .techno {
        display: flex;
        flex-flow: column nowrap;
        align-items: center;
        justify-content: center;
        margin: 5vh;
        h3 {
            text-transform: uppercase;
        }
        img {
            max-height: 140px;
        }
    }

    @media screen and (max-width: 800px) {
        .techno {
            margin: 2vh;
            img {
                height: 100px !important;
            }
        }
    }
</style>