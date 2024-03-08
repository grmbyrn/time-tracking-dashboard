<script lang="ts">
	import Card from './Card.svelte';
	import type { Post } from '$lib/utils/types';
	import { onMount } from 'svelte';
	import { selectedTime } from '$lib/stores/selectedTime';

	const changeTime = (time: string) => {
		selectedTime.set(time);
	};

	let posts: Post[] = [];
	onMount(async () => {
		posts = await getPosts();
	});

	const getPosts = async () => {
		const res = await fetch('/data/data.json');
		const data = await res.json();
		return data;
	};

	const isActive = (time: string) => {
		return $selectedTime === time ? 'active' : '';
	};
</script>

<div class="container">
	<div class="container-item-1">
		<div class="user-container">
			<div class="user-container-info">
				<div class="img-container">
					<img src="./images/image-jeremy.png" alt="user" />
				</div>
				<div class="user-container-text">
					<h3>Report for</h3>
					<h2>Jeremy Robson</h2>
				</div>
			</div>
			<div class="times-container">
				<button on:click={() => changeTime('daily')} class={isActive('daily')}>Daily</button>
				<button on:click={() => changeTime('weekly')} class={isActive('weekly')}>Weekly</button>
				<button on:click={() => changeTime('monthly')} class={isActive('monthly')}>Monthly</button>
			</div>
		</div>
	</div>

	<div class="container-item-2">
		<div class="container-table">
			<div class="container-table-item">
				{#if $selectedTime === 'daily'}
					{#each posts as post}
						<Card
							title={post.title}
							current={post.timeframes.daily.current}
							previous={post.timeframes.daily.previous}
							image={post.image}
							colour={post.color}
							time="Yesterday"
						/>
					{/each}
				{:else if $selectedTime === 'weekly'}
					{#each posts as post}
						<Card
							title={post.title}
							current={post.timeframes.weekly.current}
							previous={post.timeframes.weekly.previous}
							image={post.image}
							colour={post.color}
							time="Last week"
						/>
					{/each}
				{:else if $selectedTime === 'monthly'}
					{#each posts as post}
						<Card
							title={post.title}
							current={post.timeframes.monthly.current}
							previous={post.timeframes.monthly.previous}
							image={post.image}
							colour={post.color}
							time="Last month"
						/>
					{/each}
				{/if}
			</div>
		</div>
	</div>
</div>

<style class="container-item">
	.container {
		width: 23.4375rem;
		display: block;
		margin-left: auto;
		margin-right: auto;
		padding-top: 5rem;
		padding-inline: 1.5rem;
	}

	@media only screen and (min-width: 1200px) {
		.container {
			width: 70rem;
			display: grid;
			grid-template-columns: 1fr 3fr;
			grid-template-rows: 1fr;
			grid-column-gap: 30px;
			grid-row-gap: 0px;
		}

		.container-item-1 {
			grid-area: 1 / 1 / 2 / 2;
		}

		.container-item-2 {
			grid-area: 1 / 2 / 2 / 3;
		}
	}
	.user-container-info {
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
		transition: color 0.3s ease;
	}

	.times-container button:hover,
	.times-container button.active {
		color: #ffffff;
		cursor: pointer;
	}

	@media only screen and (min-width: 1200px) {
		.user-container {
			height: 518px;
		}
		.user-container-info {
			flex-direction: column;
			align-items: flex-start;
			height: 354px;
			top: 0px;
		}

		.user-container-text {
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
	@media only screen and (min-width: 1200px) {
		.container-table-item {
			display: grid;
			grid-template-columns: repeat(3, 1fr);
			grid-template-rows: 1fr;
			grid-column-gap: 15px;
			grid-row-gap: 30px;
		}
	}
</style>
