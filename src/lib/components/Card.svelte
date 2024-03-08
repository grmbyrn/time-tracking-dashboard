<script lang="ts">
	export let title: string;
	export let current: number;
	export let previous: number;
	export let image: string;
	export let colour: string;
	export let time: string;
</script>

<div class="container">
	<div class="icon-flex" style="background-color: {colour};">
		<img class="icon" src={image} alt="icon" />
	</div>
	<div class="inner-container">
		<div class="container-item container-item-1">
			<h2>{title}</h2>
			<img src="./images/icon-ellipsis.svg" alt="ellipsis" />
		</div>
		<div class="container-item container-item-2">
			<h1>{current}hrs</h1>
			<p>{time} - {previous}hrs</p>
		</div>
	</div>
</div>

<style>
	.container {
		padding-top: 1.75rem;
	}

	.icon-flex {
		display: flex;
		justify-content: flex-end;
		height: 50px;
		border-radius: 15px 15px 0px 0px;
		padding-right: 18px;
		overflow: hidden;
	}

	.icon {
		position: relative;
		bottom: 10px;
		height: 5rem;
	}

	.inner-container {
		background-color: #1c204b;
		border-radius: 15px;
		position: relative;
		bottom: 10px;
		padding: 1.5rem;
	}

	.inner-container:hover {
		background-color: #33397a;
	}

	.container-item {
		display: flex;
		align-items: center;
		justify-content: space-between;
		color: #ffffff;
	}

	h2 {
		font-size: 18px;
	}

	h1 {
		font-size: 2rem;
	}

	p {
		font-size: 15px;
		color: #bbc0ff;
	}

	@media only screen and (min-width: 1200px) {
		.container {
			padding-top: 0rem;
			padding-right: 0px;
			width: 250px;
			height: 244px;
		}

		.container-item-2 {
			display: flex;
			flex-direction: column;
			align-items: flex-start;
		}

		h2 {
			font-size: 18px;
		}

		h1 {
			font-size: 3.5rem;
		}

		p {
			font-size: 15px;
			color: #bbc0ff;
		}
	}
</style>
