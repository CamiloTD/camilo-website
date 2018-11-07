<template lang="pug">
    home-template(:cards="cards" v-bind:navbar-items="NavbarItems" v-bind:paragraphs="MainParagraphs" v-bind:main-buttons="MainButtons" v-bind:title="title")
</template>
<script>
    import HomeTemplate from '../template/home.vue';

    let paragraphs = [
        {
            content: '"Don\'t just create software...<br>&nbsp;Let\'s create innovation..."',
            author: "Camilo Torres",
            image: "/svg/blue-bird.svg"
        },
        {
            content: 'Forget about complex RPCs. Unete makes the things easy!',
            author: "About Unete",
            image: "/svg/network.svg"
        },
        {
            content: '¿Did you tried Booga?... It\'s like redux but a lot easier!',
            author: "About Booga",
            image: "/svg/elastic.svg"
        },
        {
            content: 'With Coraline-Educative, best gamers will be also, the smartest students... And the coolest boys in the school!',
            author: "Coraline Educative",
            image: "/svg/kid.svg"
        },
        {
            content: 'Kids can be pro very easily... Fun wrecks out duty...',
            author: "Camilo Torres",
            image: "/svg/kids.svg"
        }
    ];

    export default {
        data: () => ({
            NavbarItems: [
                { name: 'About', link: '/about' },
                { name: 'Hire us', link: '/hiring' },
                { name: 'Portfolio', link: '/products' },
                { name: 'Libraries', link: '/libraries', highlighted: true }
            ],

            MainParagraphs: paragraphs,

            MainButtons: [{ content: "Explore" }, { content: "Subscribe" }],
            cards: [
                { image: '/svg/flying-kid.svg'   , title: 'Learn'       , subtitle: 'Coraline Educative'},
                { image: '/svg/brain.svg'        , title: 'Create'      , subtitle: 'Coraline Creative' },
                { image: '/svg/pencil-rocket.svg', title: 'Explore'     , subtitle: 'Coraline Products', circular: true},
                { image: '/svg/handshake.svg'    , title: 'Work with us', subtitle: 'Contact us'}
            ],
            title: 'Coraline Project'
        }),
        components: { HomeTemplate }
    };
</script>
