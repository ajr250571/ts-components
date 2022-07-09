<script>
	import { v4 as uuidv4 } from 'uuid';

	export let value = '';
	export let label = '';
	export let error = '';

	const identifier = uuidv4();
</script>

<div class='my-2'>
	<label for={identifier} class="label">
		<span class="label-text text-secondary font-bold">{label}</span>
	</label>
	<input
		id={identifier}
		type="text"
		bind:value
		class="input input-bordered input-primary w-full max-w-xs"
		placeholder={label}
	/>
	{#if error}
		<label for={identifier} class="label">
			<span class="label-text text-white bg-warning font-semibold p-2 rounded-2xl">{error}</span>
		</label>
	{/if}
</div>
