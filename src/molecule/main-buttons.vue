<template lang="pug">
    .main-buttons
        main-button(v-for="btn in buttons" v-bind:text="btn.content")
</template>
<script>
    import MainButton from '../atom/buttons/main.vue';

    export default {
        props: ['buttons'],
        components: { MainButton }
    }
</script>

<style lang="stylus" scoped>
    .main-buttons
        display: grid
        grid-template-columns: repeat(auto-fit, minmax(220px, 1fr))
        grid-gap: 24px
        margin-top: 80px

    .main-button:first-child
        background: #C67385
    
    @media (max-device-aspect-ratio: 1/1)
        .main-button
            font-size: 16px

        @media (min-width: 768px)
            .main-button
                font-size: 40px
</style>
