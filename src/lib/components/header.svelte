<script>
	import Favicon from '$lib/assets/favicon.svg';
	import Tema from '$lib/components/tema.svelte';
</script>

<div class="header">
	<a href="https://svelte.dev/">
		<img alt="Logo do Projeto" src={Favicon} />
	</a>
	<h1>To-do List</h1>
	<Tema/>
</div>

<style>
	.header {
		position: fixed;
		top: 0;
		width: 100vw;
		height: 150px;
		background-color: #4b0082;
		color: rgb(230, 157, 98);
		display: flex;
		justify-content: space-between;
		font-size: 1.5rem;
		font-weight: bold;
	}
</style>
