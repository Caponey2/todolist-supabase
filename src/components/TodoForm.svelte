<script>
	import { addTodo } from '../stores/todoStore.js';
	import { user } from '../stores/authStore.js';
	let todo = '';
	const handleSubmit = () => {
		addTodo(todo, $user.id);
		todo = '';
		console.log('submitting');
	};
</script>

<form id="todoForm" class="my-6 flex flex-col " on:submit|preventDefault={handleSubmit}>
	<div class="flex flex-col text-sm mb-2">
		<label for="todo" class="font-bold mb-2 text-gray-800">Todo</label>
		<input
			id="todoInput"
			type="text"
			name="todo"
			placeholder="What's your to do today?"
			class="appearance-none shadow-sm border border-gray-200 p-2 focus:outline-none focus:border-gray-500 rounded-lg"
			bind:value={todo}
		/>
	</div>
	<button
		type="submit"
		class="w-full shadow-sm rounded bg-blue-500 hover:bg-blue-600 text-whtie py-2 px-4"
		>Submit</button
	>
</form>
