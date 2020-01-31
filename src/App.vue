<template>
    <div id="app">
        <single-slide-down-stairs
                v-if="activeSlide === slides.SINGLE_SLIDE_DOWN_STAIRS"
        />
        <single-slide-up-stairs
                v-if="activeSlide === slides.SINGLE_SLIDE_UP_STAIRS"
        />
        <slide-together
                v-if="activeSlide === slides.SLIDE_TOGETHER"
        />
    </div>
</template>

<script lang="ts">
    import {Component, Vue} from 'vue-property-decorator';
    import SlideTogether from '@/components/SlideTogether.vue';
    import SingleSlideUpStairs from '@/components/SingleSlideUpStairs.vue';
    import SingleSlideDownStairs from '@/components/SingleSlideDownStairs.vue';

    enum screenSlides {
        SINGLE_SLIDE_DOWN_STAIRS = 'SINGLE_SLIDE_DOWN_STAIRS',
        SINGLE_SLIDE_UP_STAIRS = 'SINGLE_SLIDE_UP_STAIRS',
        SLIDE_TOGETHER = 'SLIDE_TOGETHER',
    }

    @Component({
        components: {
            SlideTogether,
            SingleSlideUpStairs,
            SingleSlideDownStairs,
        },
    })
    export default class App extends Vue {

        public timer?: number = undefined;

        // Slide time in miliseconds
        public slideTime: number = 60000;

        public activeSlide: screenSlides = screenSlides.SINGLE_SLIDE_DOWN_STAIRS;

        public data() {
            return {
                slides: screenSlides,
            };
        }

        public mounted(): void {
            if (this.timer === undefined) {
                this.timer = window.setInterval(() => {
                    switch (this.activeSlide) {
                        case screenSlides.SINGLE_SLIDE_DOWN_STAIRS:
                            this.activeSlide = screenSlides.SINGLE_SLIDE_UP_STAIRS;
                            break;
                        case screenSlides.SINGLE_SLIDE_UP_STAIRS:
                            this.activeSlide = screenSlides.SLIDE_TOGETHER;
                            break;
                        case screenSlides.SLIDE_TOGETHER:
                            this.activeSlide = screenSlides.SINGLE_SLIDE_DOWN_STAIRS;
                            break;
                    }
                }, this.slideTime);
            }
        }

    }
</script>

<style lang="scss">
    * {
        box-sizing: border-box;
    }

    body,
    html {
        padding: 0;
        margin: 0;
        font-family: 'Lato', sans-serif;
    }
</style>
