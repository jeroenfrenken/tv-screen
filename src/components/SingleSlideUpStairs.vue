<template>
	<div class="container">
		<div class="logo left"></div>
		<div class="logo right"></div>
	</div>
</template>

<script lang="ts">
    import {Component, Vue} from 'vue-property-decorator';

    @Component
    export default class SingleSlideUpStairs extends Vue {}
</script>


<style lang="scss" scoped>
	.container {
		display: flex;
		height: 100vh;
		align-items: center;
		justify-content: center;
	}

	.logo {
		float: left;
		width: 30vw;
		height: 30vh;
		margin-left: 5vw;
		margin-right: 5vw;
		background-size: contain;
		background-repeat: no-repeat;
		background-position: center center;
	}

	.left {
		background-image: url("/assets/exitable.png");
	}

	.right {
		background-image: url("/assets/ketjapp.png");
	}
</style>
