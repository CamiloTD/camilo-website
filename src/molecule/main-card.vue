<template lang="pug">
    .main-card
        div(:class="!circular? 'image' : 'image no-border'")
            img(:src="picture")
        .description
            span.title {{title}}
            span.subtitle {{subtitle}}
</template>
<script>
export default {
    props:["picture","title","subtitle", "glow", "circular"]
}
</script>

<style lang="stylus" scoped>
.main-card
    display grid 
    grid-template-rows: 233px 132px
    justify-items:center
    width: 100%
    box-shadow: 0px 0px 10px transparentify(#5BAAFF, .65)
    cursor: pointer

    &:hover
        @keyframes src-molecule-main-card-main-card-hover-animation
            from
                transform: translateY(0) scale(1)
                box-shadow: 0px 0px 10px transparentify(#5BAAFF, .65)
            to
                transform: translateY(-10px) scale(1.05)
                box-shadow: 0px 0px 10px transparentify(#BB8BFF, .65)

        animation: src-molecule-main-card-main-card-hover-animation .25s
        transform: translateY(-10px) scale(1.05)
        box-shadow: 0px 0px 10px transparentify(#BB8BFF, .65)
    .image
        display: flex
        align-items: center
        justify-content: center
        border: 1px solid transparentify(black, 25%)
        width: 184px
        height 184px
        border-radius: 50%
        background: transparentify(#EBF1F4, 25%)
        margin-top: 22px
    
    img
        height: 136px

    .image.no-border
        border: none
        background: none

        img
            height: 151px
    
    .description
        border-top: 1px solid transparentify(black,11%)  
        width: calc(100% - 32px)
        text-align: center
    
    .title
        display: block
        font-family: Amaranth
        font-size: 32px;
    
    .subtitle
        display: block
        font-family: system-ui
        font-weight: light
        color: #2092B5
        margin-top: 19px

</style>
