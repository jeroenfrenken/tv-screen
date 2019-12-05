<template>
	<div class="slide"></div>
</template>

<script lang="ts">
    import {Component, Vue} from 'vue-property-decorator';

    @Component
    export default class SingleSlideDownStairs extends Vue {}
</script>

<style lang="scss" scoped>
	.slide {
		width: 100vw;
		height: 100vh;
		background-size: cover;
		background-repeat: no-repeat;
		background-image: url("/assets/background-mainwork-compressed.png");
	}
</style>
