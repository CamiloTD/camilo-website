<template lang="pug">
    .main
        navbar(v-bind:items="NavbarItems")
        .body
            img.logo(v-bind:src="paragraph.image")
            .right-section
                main-title.animation-fade-in
                    | {{ title }}
                    br
                    img.hidden-logo(v-bind:src="paragraph.image")
                main-quote.animation-fade-in(v-bind:content="paragraph.content" v-bind:author="paragraph.author")
                main-buttons(v-bind:buttons="MainButtons")
        
        .content
            h1 What do u wanna do today?
            .cards
                main-card(v-for="card in cards" :circular="card.circular" :picture="card.image" :title="card.title" :subtitle="card.subtitle")
            br
            br
</template>
<script>
    import Navbar from '../organism/navbar.vue';
    import MainQuote from '../molecule/main-quote.vue';
    import MainButtons from '../molecule/main-buttons.vue';
    import MainTitle from '../atom/fonts/main-title.vue';
    import MainCard from "../molecule/main-card.vue";

    let loaded = false;
    function QuoteChangeUpdate () {
        let _time = 3000;
        if(!loaded) setInterval (async () => {
                let selector = document.querySelectorAll(".main .body .right-section .main-quote, .main .body .logo, .main .body .hidden-logo");
                
                for(let i=0, element;element=selector[i++];) {
                    let _op = 1;

                    element.style.opacity = 1;
                    let timer = setInterval(() => {
                        element.style.opacity = _op -= 50/_time;
                        
                        if(_op <= 0) {
                            clearInterval(timer);
                        }
                    }, 50);
                }

                setTimeout(() => {
                    let _para;
                    do {
                        _para = this._props.paragraphs[Math.floor(Math.random() * this._props.paragraphs.length)];
                    } while(_para === this.paragraph);

                    this.paragraph = _para;

                    for(let i=0, element;element=selector[i++];) {
                        let _op = 0;

                        element.style.opacity = 0;
                        let timer = setInterval(() => {
                            element.style.opacity = _op += 50/_time;
                            
                            if(_op >= 1) {
                                clearInterval(timer);
                            }
                        }, 50);
                    }
                }, _time);

        }, 2.5 *_time);

        loaded = true;
    }

    export default {
        props: { NavbarItems: Array, paragraphs: Array, MainButtons: Array, title: String, cards: Array },
        data () {
            return {
                paragraph: this._props.paragraphs[Math.floor(Math.random() * this._props.paragraphs.length)]
            }
        },

        mounted () {
            QuoteChangeUpdate.apply(this);
        },

        components: { Navbar, MainQuote, MainButtons, MainTitle, MainCard }
    };
</script>
<style lang="stylus">
    body
        margin : 0
        padding: 0

        background: #464E57
        overflow-x hidden
</style>
<style lang="stylus" scoped>
    @require('../atom/animations/fade.styl')

    .content 
        background white
        padding-left 137px
        padding-right 137px
        h1
            font-family Amaranth
            text-align center
            font-size minmax(5vw, 72px)
            text-shadow: 0px 0px 5px transparentify(black, 1)
            border-bottom 1px solid transparentify(black, 11%)
            padding-bottom 74px
            padding-top 66px
        
        .cards
            display grid
            justify-content center
            grid-template-columns: repeat(auto-fit, minmax(220px, 1fr))
            grid-gap: 40px
    .main
        display: grid 
        grid-template-rows: 34px minmax(calc(100vh - 36px), auto) auto
        align-items: center
        box-shadow: 0 0 360px black inset

    .body
        display: grid
        grid-template-columns: 1fr 1fr
        transform: scale(.8)
        justify-items: center

        .right-section
            padding-right: 131px

    .logo, .hidden-logo
        @keyframes src-template-home-logo-bounce
            from
                filter: drop-shadow( -5px 5px 10px rgba(0,0,0,.2) ) hue-rotate(0deg) saturate(50%)
                transform: translate(0, 20px) scaleX(-1)
            
            to
                filter: drop-shadow( -5px 25px 10px rgba(0,0,0,.2) ) hue-rotate(0deg) saturate(50%)
                transform: translate(-15px, 0px) scaleX(-1)

        @keyframes src-template-home-logo-glow
            from
                filter: drop-shadow( 0px 0px 10px transparentify(white, .3)) hue-rotate(0deg) saturate(150%)
            
            to
                filter: drop-shadow( 0px 0px 10px transparentify(white, .8)) hue-rotate(360deg) saturate(150%)
        

        cursor: pointer
        height: 70vh
        filter: drop-shadow( -5px 5px 10px rgba(0,0,0,.2) )

        animation: src-template-home-logo-bounce 1s infinite alternate, fade-in 1s
        
        &:hover
            animation: src-template-home-logo-bounce 1s infinite alternate, fade-in 1s,  src-template-home-logo-glow .25s infinite alternate
            

    .hidden-logo
        display: none
    
    @media (max-width: 360px)
        .main
            box-shadow: none
        
        .body
            box-shadow: 0 0 360px black inset

    
    @media (max-device-aspect-ratio: 1/1)
        .main
            align-items: top
            width: 100vw
            height: 100vh
            box-shadow: 0 0 360px black inset
        .body
            grid-template-columns: 1fr
            transform: none
            margin-top: 48px
            z-index: -1
        
            .right-section
                padding: 35px

        .logo
            display: none 

        .hidden-logo
            display: inline
            transform: scaleX(-1)
            margin-left: 10px
            margin-top: 8vh
            margin-bottom: 5vh
            width: auto 
            height: 25vh

        .main-title
            font-size: 10vw
            margin: 0px
            text-align: center
        
        .main-buttons
            margin-top: 5vh
</style>
