<script>
	import Button from './Button.svelte';
	import { v4 as uuid } from 'uuid';

	export let todos = [];
	let taskInput = '';
	const status = ['Completed', 'Progress', 'Pending'];
	function handleTodo() {
		if (!taskInput) {
			return;
		}
		todos = [...todos, { id: uuid(), title: taskInput, status: status[2] }];
		taskInput = '';
	}
	function deleteTodo() {}
</script>

<div class="todo">
	<h2>Your To Do</h2>
	<form action="" class="todo__form" on:submit|preventDefault={handleTodo}>
		<input type="text" name="todoInput" id="todoInput" bind:value={taskInput} />
		<Button type="submit" disabled={!taskInput}>
			<span slot="content">Add</span>
		</Button>
	</form>
	<div class="todo__list">
		{#each todos as item}
			<div class="todo__item">
				<label for={item.title}>
					<input type="checkbox" name={item.title} id={item.title} />
					{item.title}
				</label>
				<Button size="sm">
					<span slot="content">❌</span>
				</Button>
			</div>
		{/each}
	</div>
</div>

<style lang="scss">
	.todo {
		&__form {
			display: flex;
			margin-bottom: var(--space-sm);
			gap: var(--space-2xsm);
			input {
				padding: 8px;
				outline: none;
				border: 1px solid var(--color-border-light);
				border-radius: var(--round-sm);
				width: 100%;
			}
		}
		width: 400px;

		&__list {
			display: flex;
			flex-direction: column;
			gap: 20px;
			user-select: none;
		}

		&__item {
			display: flex;
			justify-content: flex-start;
			align-items: center;
			padding: var(--space-2xsm);
			border: 1px solid var(--color-border-light);
			border-radius: var(--round-md);
			label {
				text-align: left;
				flex-grow: 1;
			}
		}
	}
</style>
