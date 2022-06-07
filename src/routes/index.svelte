<script context="module">
	export const prerender = true;
</script>

<script>
	import Counter from '$lib/Counter.svelte';
	import Quote from '$lib/components/quotes.svelte';
	export let quotes;
</script>

<svelte:head>
	<title>Home</title>
	<meta name="description" content="Svelte demo app" />
</svelte:head>

<section>
	<h1>
		<div class="welcome">
			<picture>
				<source srcset="svelte-welcome.webp" type="image/webp" />
				<img src="svelte-welcome.png" alt="Welcome" />
			</picture>
		</div>

		<!-- to your new<br />SvelteKit app -->
	</h1>

	<!-- <h2>
		try editing <strong>src/routes/index.svelte</strong>
	</h2> -->

	<!-- <Counter /> -->
	<div class="flex flex-col text-center space-y-4 pb-3">
		<div class="container">
			{#await quotes}
				<p>Loading quotes...</p>
			{:then quotes}
				<Quote {quotes} />
			{:catch error}
				<p>{error.message}</p>
			{/await}
		</div>
	</div>
</section>

<style>
	section {
		display: flex;
		flex-direction: column;
		justify-content: center;
		align-items: center;
		flex: 1;
	}

	h1 {
		width: 100%;
	}

	.welcome {
		position: relative;
		width: 100%;
		height: 0;
		padding: 0 0 calc(100% * 495 / 2048) 0;
	}

	.welcome img {
		position: absolute;
		width: 100%;
		height: 100%;
		top: 0;
		display: block;
	}
</style>
