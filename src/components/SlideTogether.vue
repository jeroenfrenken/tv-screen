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
		<div class="news">
			<div class="time">
				<p>12:00</p>
			</div>
			<div class="news-items">

			</div>
		</div>
	</div>
</template>

<script lang="ts">
    import {Component, Vue} from 'vue-property-decorator';

    @Component
    export default class SlideTogether extends Vue {}
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

	.news {

		.time {
			height: 5vh;
			display: flex;
			align-items: center;
			justify-content: center;
			width: 7vw;
			color: #ffffff;
			background-color: #000000;
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
