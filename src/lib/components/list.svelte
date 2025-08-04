<script lang="ts">
	import Todo from '$lib/components/todo.svelte';
	import AddTodo from '$lib/components/add-todo.svelte';

	let { list } = $props();

	const deleteTodo = (todoToRemove) => {
		const index = list.indexOf(todoToRemove);
		list.splice(index, 1);
	};

	const editTodo = (todo, newTodo) => {
		if (list.some((td) => !td.completed && todo != td && td.text === newTodo)) {
			alert('Já existe essa tarefa!');
			return false;
		}
		todo.text = newTodo;
		return true;
	};
</script>

<AddTodo {list} />

{#each list as todo}
	<Todo {editTodo} {todo} {deleteTodo} />
{/each}
