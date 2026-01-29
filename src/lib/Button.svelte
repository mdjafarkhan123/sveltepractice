<script>
	export let size = 'none';
</script>

<button {...$$restProps} on:click class:large={size === 'lg'} class:small={size === 'sm'}>
	<slot name="content"></slot>
</button>
