<template lang="pug">
    .navbar-menus
        basic-button(v-for="item in items" v-bind:name="item.name" v-bind:highlight="item.highlighted")
</template>
<script>
import BasicButton from '../atom/buttons/basic.vue'

export default {
    components: { BasicButton },
    props: ['items']
}
</script>

<style lang="stylus" scoped>
    .navbar-menus
        text-align: right
        
    button
        margin-left: 10px
        margin-right: 10px

    button.highlight
        margin-left: 16px
</style>

