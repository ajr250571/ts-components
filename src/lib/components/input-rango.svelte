<script>
	import { v4 as uuidv4 } from 'uuid';

	export let label = '';

	export let value = 0;
	export let min = 0;
	export let max = 99999999;
	export let step = 1;
	export let error = '';

	const identifier = uuidv4();

	let formatter = new Intl.NumberFormat('es-CL');
</script>

<div>
	<label for={identifier} class="label">
		<span class="label-text text-primary font-bold">{label}</span>
	</label>
	<input
		id={identifier}
		type="range"
		bind:value
		class="range range-bordered range-primary w-full max-w-xs"
		placeholder={label}
		{min}
		{max}
		{step}
	/>
	<span
		class="text text-border text-primary rounded-md w-full max-w-xs font-bold mx-2 text-center align-top"
		>{formatter.format(value)}/{formatter.format(max)}</span
	>
	{#if error}
		<label for={identifier} class="label">
			<span class="label-text text-white bg-error font-semibold p-2 rounded-b-2xl">❌ {error}</span>
		</label>
	{/if}
</div>
