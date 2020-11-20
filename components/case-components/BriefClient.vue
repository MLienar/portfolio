<template>
  <div class="brief-client">
      <img :src="require(`~/assets/${mockup}.png`)" :alt="alt">
      <div class="text-brief">
          <h2>Brief Client</h2>
          <p><slot></slot></p>
      </div>
  </div>
</template>

<script>
export default {
    name: 'BriefClient',
    props: ['mockup', 'alt']
}
</script>

<style lang="scss">
    .brief-client {
        width: 80%;
        margin: 15vh auto 10vh auto;
        display: flex;
        flex-flow: row nowrap;
        justify-content: center;
        align-items: center;
        img {
            width: 50%;
            height: auto;
            max-width: 700px;
            margin-right: 2.5vh;
        }
        .text-brief {
            padding: 0 0 0 5vh;
            display: flex;
            flex-flow: column nowrap;
            justify-content: center;
            margin-left: 2.5vh;
        
            h2 {
                margin-bottom: 3vh;
                text-transform: uppercase;
            }
            p {
                max-width: 600px;
            }
        }
    }

    @media screen and (max-width: 800px) {
        .brief-client {
        flex-flow: column nowrap;
        padding: 0 !important;
        text-align: center;
        img {
            width: 90%;
            margin-bottom: 5vw;
            margin-right: 0;
        }
        }
        .text-brief {
        padding: 0 !important;
        margin: 0 !important;
        }
    }

</style>