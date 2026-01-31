<script>
	import { v4 as uuid } from 'uuid';
	import svelteLogo from './assets/svelte.svg';
	import Todo from './lib/Todo.svelte';
	let status = ['Completed', 'Pending'];
	let todos = [
		{
			id: uuid(),
			title: 'Shopping',
			status: status[1]
		},
		{
			id: uuid(),
			title: 'Doctor',
			status: status[0]
		},
		{
			id: uuid(),
			title: 'Walking',
			status: status[2]
		},
		{
			id: uuid(),
			title: 'Market',
			status: status[0]
		}
	];

	function handleTodo(e) {
		e.preventDefault();
		todos = [...todos, { id: uuid(), title: e.detail.task, status: 'Progress' }];
	}
	function handleRemove(e) {
		todos = todos.filter((item) => {
			return item.id !== e.detail.id;
		});
	}
</script>

<img src={svelteLogo} alt="svelte logo" width="100" height="100" />
<Todo {todos} on:addtodo={handleTodo} on:removeTodo={handleRemove}></Todo>
<div>Your remaining todos: {todos.length}</div>
