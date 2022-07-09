<script>
	import InputNumber from '$lib/components/input-number.svelte';

	import InputText from '../lib/components/input-text.svelte';

	let minimoSueldoBasico = 60000;
	let fields = {
		nombre: 'Armando Javier',
		apellido: 'Rodriguez',
		sueldoBasico: 150000
	};
	let errors = {
		nombre: '',
		apellido: '',
		sueldoBasico: ''
	};

	let valid = false;

	function handleSubmit() {
		valid = true;

		if (fields.nombre.trim().length < 1) {
			errors.nombre = 'El Nombre no puede estar vacio.';
			valid = false;
		} else {
			errors.nombre = '';
		}
		if (valid) {
			console.log(fields);
		}

		if (fields.apellido.trim().length < 1) {
			errors.apellido = 'El Apellido no puede estar vacio.';
			valid = false;
		} else {
			errors.apellido = '';
		}

		if (fields.sueldoBasico < minimoSueldoBasico) {
			errors.sueldoBasico = `El Sueldo Basico NO puede ser menor a $ ${Intl.NumberFormat().format(
				minimoSueldoBasico
			)}`;
			valid = false;
		} else {
			errors.sueldoBasico = '';
		}

		console.log(valid);
		if (valid) {
			console.log(fields);
		}
	}
</script>

<h1 class="font-bold text-primary text-4xl">Bienvenido a SvelteKit</h1>

<form on:submit|preventDefault={handleSubmit}>
	<InputText label="Nombre" bind:value={fields.nombre} error={errors.nombre} />
	<InputText label="Apellido" bind:value={fields.apellido} error={errors.apellido} />
	<InputNumber
		label="Sueldo Basico"
		bind:value={fields.sueldoBasico}
		error={errors.sueldoBasico}
		min={0}
		step={1}
	/>

	<input type="submit" value="Enviar" class="btn btn-primary" />
</form>
