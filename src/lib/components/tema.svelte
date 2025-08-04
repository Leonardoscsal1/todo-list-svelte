<script>
	function mudarTema() {
		window.document.body.classList.toggle('dark-mode');
	}
</script>

<button onclick={mudarTema}> Tema </button>

<style>
	button {
		background-color: rgb(228, 218, 218);
		color: black;
		border: none;
		border-radius: 30px;
		margin: 50px;
		padding: 15px;
		text-transform: uppercase;
		cursor: pointer;
	}
	:global(body.dark-mode) button {
		background-color: rgb(32, 18, 70);
		color: white;
	}
</style>
