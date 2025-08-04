<script lang="ts">
	type Todo = { text: string; completed: boolean };

	let { list }: { list: Todo[] } = $props();
	let newTodo = $state('');

	const addTodo = () => {
		if (list.some((todo) => !todo.completed && todo.text == newTodo.trim())) {
			alert('Não pode adicionar a mesma tarefa!');
			return;
		}
		if (!newTodo.trim()) {
			alert('A tarefa não pode está vazia!');
			return;
		}
		list.push({ text: newTodo, completed: false });
		newTodo = '';
	};
</script>

<h2>Tarefas</h2>
<input
	type="text"
	bind:value={newTodo}
	onkeydown={(e) => {
		if (e.key === 'Enter') {
			addTodo();
		}
	}}
/>
<button onclick={addTodo}>Adicionar tarefas</button>

<style>
	h2 {
		text-align: start;
		color: purple;
		margin-top: 5px;
		margin-bottom: 15px;
		font-weight: 900;
	}

	input[type='text'] {
		padding: 10px;
		font-size: 1rem;
		width: 67%;
		border: 1px solid #ccc;
		border-radius: 8px;
		margin-right: 10px;
	}

	button {
		padding: 10px 20px;
		font-size: 1rem;
		background-color: #4b0082;
		color: white;
		border: 0;
		border-radius: 15px;
		cursor: pointer;
		transition: background 0.3s ease;
	}

	button:hover {
		background-color: #9812f8;
	}
</style>
