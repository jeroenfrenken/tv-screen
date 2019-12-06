<template>
    <div>
        <div class="container">
            <div class="card">
                <h1>Begane grond</h1>
                <img src="/assets/mainwork-logo.png">
            </div>
            <div class="card">
                <h1>Eerste verdieping</h1>
                <img src="/assets/exitable.svg">
                <img src="/assets/ketjapp.svg">
            </div>
        </div>
        <div class="ticker-wrap">
            <div class="ticker">
                <div
                    class="ticker__item"
                    :key="key"
                    v-for="(item, key) in items"
                >{{ item.title }}</div>
            </div>
        </div>
    </div>
</template>

<script lang="ts">
    import Parser from 'rss-parser';
    import { Component, Vue } from 'vue-property-decorator';

    @Component
    export default class SlideTogether extends Vue {

        public items: {
            title: string
        }[] = [];

        public async mounted() {
            const parser = new Parser();
            const CORS_PROXY = 'https://cors-anywhere.herokuapp.com/';
            let feed: any = await parser.parseURL(CORS_PROXY + 'https://www.nu.nl/rss/Algemeen');

            feed.items.forEach((item: any) => {
                this.items.push({
                    title: item.title
                });
            });
        }

    }
</script>

<style lang="scss" scoped>
    .container {
        height: 95vh;
        display: flex;
        align-items: center;
        justify-content: center;
        background-size: cover;
        background-position: center center;
        background-repeat: no-repeat;
        background-image: url("/assets/background-office.jpg");
    }

    $duration: 120s;

    @-webkit-keyframes ticker {
        0% {
            -webkit-transform: translate3d(0, 0, 0);
            transform: translate3d(0, 0, 0);
            visibility: visible;
        }

        100% {
            -webkit-transform: translate3d(-100%, 0, 0);
            transform: translate3d(-100%, 0, 0);
        }
    }

    @keyframes ticker {
        0% {
            -webkit-transform: translate3d(0, 0, 0);
            transform: translate3d(0, 0, 0);
            visibility: visible;
        }

        100% {
            -webkit-transform: translate3d(-100%, 0, 0);
            transform: translate3d(-100%, 0, 0);
        }
    }

    .ticker-wrap {
        position: fixed;
        bottom: 0;
        width: 100%;
        overflow: hidden;
        height: 5vh;
        background-color: rgba(#000, 0.9);
        padding-left: 100%;
        box-sizing: content-box;

        .ticker {

            display: inline-block;
            height: 5vh;
            line-height: 5vh;
            white-space: nowrap;
            padding-right: 100%;
            box-sizing: content-box;

            -webkit-animation-iteration-count: infinite;
            animation-iteration-count: infinite;
            -webkit-animation-timing-function: linear;
            animation-timing-function: linear;
            -webkit-animation-name: ticker;
            animation-name: ticker;
            -webkit-animation-duration: $duration;
            animation-duration: $duration;

            &__item {

                display: inline-block;

                padding: 0 1.5rem;
                font-size: 1.5rem;
                color: white;

            }

        }

    }

    .card {
        background-color: #ffffff;
        width: 30vw;
        text-align: center;
        margin-left: 5vw;
        margin-right: 5vw;
        height: 60vh;
        padding: 5px;
        border-radius: 5px;

        img {
            display: block;
            margin: 5vh auto;
            width: 20vw;
        }
    }
</style>
