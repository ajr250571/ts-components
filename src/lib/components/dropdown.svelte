<script>
	import { v4 as uuidv4 } from 'uuid';

	export let label = '';
	export let choices = [''];
	export let value = '';
	export let error = '';

	const identifier = uuidv4();
</script>

<div class="my-2">
	<label for={identifier} class="label">
		<span class="label-text text-primary font-bold">{label}</span>
	</label>
	<select id={identifier} bind:value class="select select-bordered select-primary w-full max-w-xs ">
		{#each choices as choice}
			<option value={choice}>{choice}</option>
		{/each}
	</select>
	{#if error}
		<label for={identifier} class="label">
			<span class="label-text text-white bg-error font-semibold p-2 rounded-b-2xl">❌ {error}</span>
		</label>
	{/if}
</div>
