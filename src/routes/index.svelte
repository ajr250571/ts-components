<script>
	import Dropdown from '$lib/components/dropdown.svelte';
	import InputNumber from '$lib/components/input-number.svelte';
	import InputRango from '$lib/components/input-rango.svelte';
	import InputText from '$lib/components/input-text.svelte';

	let minimoSueldoBasico = 60000;
	let fields = {
		nombre: '',
		apellido: '',
		sueldoBasico: 0,
		categoria: 'Efectivo',
		rango: 1
	};
	let errors = {
		nombre: '',
		apellido: '',
		sueldoBasico: '',
		categoria: '',
		rango: ''
	};

	const CATEGORIA_CHOICE = ['Efectivo', 'Contratado'];

	let valid = false;

	function handleSubmit() {
		valid = true;

		if (fields.nombre.trim().length < 1) {
			errors.nombre = 'El Nombre no puede estar vacio.';
			valid = false;
		} else {
			errors.nombre = '';
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

		if (valid) {
			console.log('Valid', fields);
		}
	}
</script>

<div class="container mx-auto px-2 py-2" data-theme="cupcake">
	<div class="flex justify-around gap-2">
		<div>
			<h1 class="font-bold text-primary text-4xl">Bienvenido a SvelteKit</h1>

			<form on:submit|preventDefault={handleSubmit}>
				<InputText label="Nombre" bind:value={fields.nombre} error={errors.nombre} />
				<InputText label="Apellido" bind:value={fields.apellido} error={errors.apellido} />
				<InputNumber
					label="Sueldo Basico"
					bind:value={fields.sueldoBasico}
					error={errors.sueldoBasico}
					min={0}
					max={999999}
					step={1}
				/>
				<Dropdown
					label="Categoria"
					bind:value={fields.categoria}
					error={errors.categoria}
					choices={CATEGORIA_CHOICE}
				/>
				<InputRango
					label="Rango"
					bind:value={fields.rango}
					error={errors.rango}
					min={1}
					max={1000}
					step={1}
				/>

				<input type="submit" value="Enviar" class="btn btn-primary my-4" />
			</form>
		</div>
	</div>
</div>
