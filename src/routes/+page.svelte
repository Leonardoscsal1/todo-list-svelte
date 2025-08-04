<script lang="ts">
	import Header from '$lib/components/header.svelte';
	import List from '$lib/components/list.svelte';
	type Todo = { text: string; completed: boolean };
	const list:Todo[] = $state([]);
</script>

<main>
	<Header />
	<div class="container">
		<List {list} />
	</div>
</main>

<style>
	:global(body) {
		margin: 0;
		font-family: 'Segoe UI', sans-serif;
		background-color: rgb(228, 218, 218);
		transition: background-color 0.3s;
	}

	:global(body.dark-mode) {
		background-color: rgb(32, 18, 70);
		color: black;
	}

	main {
		margin: 0;
		padding: 0;
		display: flex;
		flex-direction: column;
		align-items: center;
		justify-content: center;
		padding-top: 18%;
	}

	.container {
		background-color: white;
		padding: 20px;
		border-radius: 20px;
		width: 100%;
		max-width: 600px;
	}
</style>
