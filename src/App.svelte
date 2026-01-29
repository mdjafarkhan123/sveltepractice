<script>
	import { v4 as uuid } from 'uuid';
	import svelteLogo from './assets/svelte.svg';
	import Todo from './lib/Todo.svelte';
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

	$: console.log(todos);
</script>

<img src={svelteLogo} alt="svelte logo" width="100" height="100" />
<Todo bind:todos></Todo>
<div>Your remaining todos: {todos.length}</div>
