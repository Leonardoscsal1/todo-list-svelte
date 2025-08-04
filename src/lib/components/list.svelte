<script lang="ts">
	import Todo from '$lib/components/todo.svelte';
	import AddTodo from '$lib/components/add-todo.svelte';
	type TodoType = { text: string; completed: boolean };

	let { list }: { list: TodoType[] } = $props();

	function deleteTodo(todoToRemove: TodoType) {
		const index = list.indexOf(todoToRemove);
		list.splice(index, 1);
	}

	function editTodo(todo: TodoType, newTodo: string): boolean {
		if (list.some((td) => todo != td && td.text === newTodo)) {
			alert('Já existe essa tarefa!');
			return false;
		}
		todo.text = newTodo;
		return true;
	}
</script>

<AddTodo {list} />

{#each list as todo}
	<Todo {editTodo} {todo} {deleteTodo} />
{/each}
