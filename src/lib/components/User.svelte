<script lang="ts">
	import { selectedTime } from '$lib/stores/selectedTime';

	const changeTime = (time: string) => {
		selectedTime.set(time);
	};
</script>

<div class="container">
	<div class="user-container">
		<div class="img-container">
			<img src="./images/image-jeremy.png" alt="user" />
		</div>
		<div class="text-container">
			<h3>Report for</h3>
			<h2>Jeremy Robson</h2>
		</div>
	</div>
	<div class="times-container">
		<button on:click={() => changeTime('daily')}>Daily</button>
		<button on:click={() => changeTime('weekly')}>Weekly</button>
		<button on:click={() => changeTime('monthly')}>Monthly</button>
	</div>
</div>

<style>
	.user-container {
		display: flex;
		align-items: center;
		background-color: #5747ea;
		padding: 2.125rem 2rem;
		gap: 1.25rem;
		border-radius: 15px;
		position: relative;
		top: 15px;
	}

	h3,
	h2 {
		margin: 2px;
	}

	h3 {
		font-size: 15px;
		color: #bbc0ff;
	}

	h2 {
		font-size: 1.5rem;
		color: #ffffff;
	}

	img {
		height: 78px;
		border: 4px solid #ffffff;
		border-radius: 50%;
	}

	.times-container {
		display: flex;
		justify-content: space-between;
		padding-inline: 1.5rem;
		background-color: #1c204b;
		border-radius: 15px;
		margin-top: -15px;
	}

	.times-container button {
		color: #7078c9;
		background-color: transparent;
		border: none;
		font-family: 'Rubik', sans-serif;
		padding-block: 3rem 1.5rem;
		text-align: left;
	}

	.times-container button:hover {
		color: #ffffff;
		cursor: pointer;
	}

	@media only screen and (min-width: 1200px) {
		.container {
			height: 518px;
		}
		.user-container {
			flex-direction: column;
			align-items: flex-start;
			height: 354px;
			top: 0px;
		}

		.text-container {
			margin-top: 2.5rem;
		}

		h2 {
			font-size: 2.5rem;
			margin-top: 0.5rem;
		}

		.times-container {
			flex-direction: column;
			padding-block: 3.5rem 0.9rem;
			margin-top: -45px;
		}

		.times-container button {
			padding-block: 0.85rem;
		}
	}
</style>
