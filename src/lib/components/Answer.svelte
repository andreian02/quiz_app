<script>
	export let handleKeyup;
	export let value;
</script>

<div class="flex flex-row justify-center space-x-4 mx-4">
	<input
		type="text"
		class="max-w-lg w-full p-4 my-2 border border-gray-300 rounded-md"
		placeholder="type your answer here"
		bind:value
		on:keyup|preventDefault={handleKeyup}
	/>
</div>
