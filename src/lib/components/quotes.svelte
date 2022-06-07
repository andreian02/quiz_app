<script>
	import data from '../../assets/quotes.json';

	import { fade } from 'svelte/transition';
	let options = { duration: 400 };

	export let quotes = data;
	let quote = getRandomQuote(quotes);

	function getRandomQuote(quotes) {
		return quotes[Math.floor(Math.random() * quotes.length)];
	}

	function updateQuote() {
		quote = getRandomQuote(quotes);
	}
</script>

<div class="box">
	<blockquote>
		{#key quote}
			<div in:fade={options}>
				<p class="quote name">{quote.author}:</p>
				<p class="quote content">{quote.quote}</p>
			</div>
		{/key}
	</blockquote>
</div>

<button
	class="ml-auto px-2 py-1 border border-gray-200 bg-gray-200 text-gray-700 rounded-md hover:bg-red-500 hover:text-white"
	on:click={updateQuote}
	type="submit"
>
	<span class="icon"><i class="fas fa-redo" /></span>
	<span>取下一个卦</span>
</button>

<style>
	footer {
		font-weight: 500;
		margin-left: 3rem;
	}
	footer::before {
		content: '\2014 ';
	}
	blockquote {
		margin-bottom: 2rem;
	}
</style>
