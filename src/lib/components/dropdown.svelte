<script>
	import { v4 as uuidv4 } from 'uuid';

	export let label = '';
	export let choices = '';
	export let value = '';
	export let error = '';

	const identifier = uuidv4();
</script>

<div>
	<label for={identifier}>{label}</label>
	<select id={identifier} bind:value>
		{#each choices as choice}
			<option value={choice}>{choice}</option>
		{/each}
	</select>
	<div>{error}</div>
</div>
