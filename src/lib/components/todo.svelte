<script lang="ts">
	type Todo = { text: string; completed: boolean };
	let {
		todo,
		deleteTodo,
		editTodo
	}: {
		todo: Todo;
		deleteTodo: (td: Todo) => void;
		editTodo: (td: Todo, newTodo: string) => boolean;
	} = $props();
	let isEditing = $state(false);
	let newTodo = $state('');
	function confirmChange() {
		const success = editTodo(todo, newTodo);
		if (success) {
			isEditing = false;
		}
	}
</script>

<p>
	<input type="checkbox" bind:checked={todo.completed} />
	{#if !isEditing}
		{todo.text}
		<span class="button-group">
			<button onclick={() => (isEditing = true)}>Editar</button>
			<button onclick={() => deleteTodo(todo)}>Remover</button>
		</span>
	{:else}
		<input
			type="text"
			bind:value={newTodo}
			onkeydown={(e) => {
				if (e.key === 'Enter') {
					confirmChange();
				}
			}}
		/>
		<span class="button-group">
			<button onclick={confirmChange}>Confirmar</button>
			<button onclick={() => deleteTodo(todo)}>Remover</button>
		</span>
	{/if}
</p>

<style>
	p {
		background-color: whitesmoke;
		border: 1px solid rgb(220, 220, 220);
		padding: 12px;
		border-radius: 8px;
		display: flex;
		align-items: center;
		justify-content: space-between;
		gap: 10px;
		margin-bottom: 10px;
		flex-wrap: wrap;
	}

	input[type='checkbox'] {
		margin-right: 10px;
		transform: scale(1.3);
	}

	.button-group {
		display: flex;
		gap: 10px;
		margin-top: 5px;
		justify-content: flex-end;
		flex-wrap: wrap;
	}

	input[type='text'] {
		flex-grow: 1;
		height: 25px;
		font-size: 1rem;
		border-radius: 5px;
		border: 1px solid #ccc;
	}

	button {
		padding: 5px 10px;
		border: none;
		border-radius: 6px;
		cursor: pointer;
		background-color: #4b0082;
		color: white;
		transition: background 0.3s ease;
	}

	button:hover {
		background-color: #9812f8;
	}

	button:disabled {
		background-color: #ccc;
		cursor: not-allowed;
	}
</style>
