<template lang="pug">
    .navbar
        img.logo(src="/svg/blue-bird.svg")
        navbar-menus(v-bind:items="items")

</template>
<script>
import NavbarMenus from '../molecule/navbar-menus'

export default {
    components: { NavbarMenus },
    props: ['items']
}
</script>

<style lang="stylus" scoped>
    .navbar
        display: grid
        grid-template-columns: 70px 1fr
        align-items: center

        width: calc(100% - 2px)
        height: 100%

        background: transparentify(white, 1)
        box-shadow: 0px 2px 5px rgba(0,0,0,.2)

        border-radius: 5px
        border: 1px solid transparentify(black, .2)

    .logo
        height: 60%
        margin-left: 8px

        transform: scaleX(-1)
    
    @media (max-width: 425px)
        .navbar
            grid-template-columns: 1fr
            .logo
                display: none
            .navbar-menus
                text-align: center

</style>
