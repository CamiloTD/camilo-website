<template lang="pug">
    button(v-bind:class="highlight? 'highlight': ''") {{ name }}
</template>

<script>
export default {
    props: ['name', 'highlight']
}
</script>

<style lang="stylus" scoped>
    @import url('https://fonts.googleapis.com/css?family=Amaranth');
    
    button
        border: none 
        background: none
        color: transparentify(black, 1)
        font-family: Amaranth
        font-size: 18px
        opacity: .7
        cursor: pointer

        &:hover
            text-shadow: 0px 0px 5px transparentify(white, .5)

    .highlight
        color: transparentify(black, .5)
        background: #96C9BA
        opacity: 1
        border-radius: 9px
        width: 160px
        box-shadow: 0px 0px 4px transparentify(black, .3)

        &:hover
            color: transparentify(black, .7)
            text-shadow: none
            box-shadow: 0px 0px 10px transparentify(lighten(#96C9BA, 10), 1)
        
    @media (max-width: 425px)
        .highlight
            width: 90px
</style>
