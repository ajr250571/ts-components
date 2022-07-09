<script>
	import { v4 as uuidv4 } from 'uuid';

	export let value = 0;
	export let label = '';
	export let min = 0;
	export let max = 999999999;
	export let step = 0.01;
	export let error = '';

	const identifier = uuidv4();
</script>

<div class="my-2">
	<label for={identifier} class="label">
		<span class="label-text text-primary font-bold">{label}</span>
	</label>
	<input
		id={identifier}
		type="number"
		bind:value
		class="input input-bordered input-primary w-full max-w-xs"
		placeholder={label}
		{min}
		{max}
		{step}
	/>
	{#if error}
		<label for={identifier} class="label">
			<span class="label-text text-white bg-error font-semibold p-2 rounded-b-2xl">❌ {error}</span>
		</label>
	{/if}
</div>
