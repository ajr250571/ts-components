<script>
	import { v4 as uuidv4 } from 'uuid';

	export let label = '';

	export let value = 0;
	export let min = 0;
	export let max = 99999999;
	export let step = 1;
	export let error = '';

	const identifier = uuidv4();
</script>

<div>
	<label for={identifier}>{label}</label>
	<input type="range" id={identifier} {min} {max} {step} bind:value />
	<span>{Intl.NumberFormat().format(value)}</span>
	<div>{error}</div>
</div>
