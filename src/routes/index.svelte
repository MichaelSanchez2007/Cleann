<script>
	import Header from '$lib/Header.svelte';
	import { fly, slide } from 'svelte/transition';
	import { onMount } from 'svelte';

	let mounted = false;
	onMount(() => {
		mounted = true;
	});
</script>

<Header />

<h3>
	<span>M</span>
	<span>i</span>
	<span>c</span>
	<span>h</span>
	<span>a</span>
	<span>e</span>
	<span>l</span>
	<hr />
	<span>F</span>
	<span>r</span>
	<span>a</span>
	<span>c</span>
	<span>t</span>
	<span>a</span>
	<span>l</span>
</h3>

<div class="homepage">
	<div class="content">
		<h1>
			{#if mounted}
				{#each 'Ontario' as letter, i}
					<div class="letter" in:fly={{ y: 20, delay: i * 100, duration: 1000 }}>
						{letter}
					</div>
				{/each}
			{/if}
		</h1>

		{#if mounted}
			<hr />
			<h2 in:slide={{ delay: 500, duration: 1000 }}>Downtown Toronto</h2>
			<hr />
		{/if}
	</div>
</div>

<div class="background" />

<style>
	.background {
		position: absolute;
		inset: 0;
		width: 100vw;
		max-height: 100vh;
		margin: 0;
		background-image: url('/CN.jpg');
		background-repeat: no-repeat;
		background-size: cover;
		z-index: -1;
	}
	@media only screen and (min-width: 1250px) {
		.background {
			background-image: url('Medium.jpg');
			background-position: 50% 60%;
		}
	}
	.homepage {
		display: flex;
		position: relative;
		width: 100vw;
		height: 100vh;
		max-height: 100vw;
		flex-grow: 1;
		align-items: center;
		justify-content: center;
		flex-direction: column;
	}
	h1,
	h2 {
		position: relative;
		font-family: 'Questrial', sans-serif;
		color: white;
		font-weight: 500px;
		font-size: 150px;
		width: 600px;
		margin: auto;
		letter-spacing: 5px;
		height: max-content;
		text-align: center;
	}
	h1 {
		display: flex;
		margin: auto;
		width: max-content;
		cursor: default;
	}
	h2 {
		font-size: 20px;
		/* border: 1px solid white; */
		padding: 5px 0;
	}
	h3 {
		position: absolute;
		right: 1rem;
		color: white;
		font-family: 'Questrial', sans-serif;
		z-index: 10;
		cursor: default;
		text-align: center;
	}
	span,
	.letter {
		transition: 1s;
	}
	span:hover,
	.letter:hover {
		transition: 0.2s;
		color: black;
	}
</style>
