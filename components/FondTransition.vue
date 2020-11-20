<template>
   <div class="fond-transition"></div>
   
</template>

<script>
export default {
    name: 'FondTransition'
}
</script>

<style>
    .fond-transition {
        background: var(--lightbeige);
        position: fixed;
        z-index: 10;
    } 
    .index .fond-transition {
        left: 0;
        top: 0;
        width: 100vw;
        height: 100vh;
    }

    .case-page .fond-transition {
        right: 0;
        top: 0;
        width: 100vw;
        height: 0;
    }
</style>