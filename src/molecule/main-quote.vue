<template lang="pug">
    .main-quote
        .content(v-html="content" v-bind:style="`font-size: ${(29)/Math.sqrt(content.split('<br>')[0].length)}vw`")
        .author - {{ author }}
</template>
<script>
export default {
    props: ['content', 'author']
}
</script>

<style lang="stylus" scoped>
    .main-quote
        display: block
        
        .content, .author
            font-family: Amaranth 
            font-style: italic

        .content
            color: transparentify(white, .94)
            text-shadow: 0px 0px 5px transparentify(black, .65)
        
        .author
            color: transparentify(white, .7)
            font-size: 1.5vw
            text-shadow: 0px 0px 2px transparentify(black, .65)
            text-align: right
            margin-right: 3vw
        
        @media (max-device-aspect-ratio: 1/1)
                .content
                    text-align: center
                
                .author
                    font-size: 2vw
</style>
