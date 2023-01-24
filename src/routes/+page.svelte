<script>
	import TodoForm from '../components/TodoForm.svelte';
	import { todos } from '../stores/todoStore.js';
	import Todo from '../components/Todo.svelte';
</script>

<main id="mainContainer" class="flex flex-col items-center w-screen">
	<h1 class="text-2xl font-bold text-center text-gray-800 md:text-3xl">My Todos</h1>
	<TodoForm
		id="todoForm
    "
	/>
	{#each $todos as todo}
		<Todo {todo} index={todo.id} />
	{/each}
</main>
