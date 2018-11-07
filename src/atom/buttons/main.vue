<template lang="pug">
    button.main-button {{ text }}
</template>
<script>
export default {
    props: ['text']
}
</script>

<style lang="stylus" scoped>
    button 
        width: 100%
        color: white
        font-size: 32px
        border: none
        border-radius: 7px
        font-family: Amaranth
        background: #7398C6
        padding: 12px
        box-shadow: 5px 5px 10px transparentify(black, .3)
        cursor: pointer

        &:hover
            text-shadow: 0px 0px 10px transparentify(white, .7)
</style>