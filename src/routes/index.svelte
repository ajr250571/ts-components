<script>
	import InputCombobox from '$lib/components/input-combobox.svelte';
	import InputCheckbox from '$lib/components/input-checkbox.svelte';
	import InputNumber from '$lib/components/input-number.svelte';
	import InputRango from '$lib/components/input-rango.svelte';
	import InputText from '$lib/components/input-text.svelte';
	import InputSelectbox from '$lib/components/input-selectbox.svelte';

	let minimoSueldoBasico = 60000;
	let fields = {
		nombre: 'Armando Javier',
		apellido: 'Rodriguez',
		sueldoBasico: 150000,
		categoria: 'Quincenal',
		rango: 3,
		activo: true,
		perfiles: ['Admin','Invitado']
	};
	let errors = {
		nombre: '',
		apellido: '',
		sueldoBasico: '',
		categoria: '',
		rango: '',
		activo: '',
		perfiles: ''
	};

	const CATEGORIA_CHOICE = ['Mensual', 'Quincenal', 'Agencia', 'Eventual'];
	const PERFILES_CHOICE = ['Admin', 'Invitado', 'Balanza', 'Hilatura', 'Tejeduria', 'Urdido'];

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

		if (fields.perfiles.length < 1) {
			errors.perfiles = 'Perfiles no puede estar vacio, seleccione por lo menos uno.';
			valid = false;
		} else {
			errors.perfiles = '';
		}

		if (valid) {
			console.log('Valid', fields);
		}
	}
</script>

<main class="container mx-auto px-2 py-2" data-theme="retro">
	<div class="flex justify-around gap-2">
		<div>
			<h1 class="font-bold text-secondary text-4xl">SvelteKit</h1>

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
				<InputCombobox
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
					max={5}
					step={1}
				/>
				<InputCheckbox label="¿ Está Activo ?" bind:checked={fields.activo} error={errors.activo} />

				<InputSelectbox
					label="Perfiles"
					bind:value={fields.perfiles}
					error={errors.perfiles}
					choices={PERFILES_CHOICE}
				/>

				<input type="submit" value="Enviar" class="btn btn-primary my-4" />
			</form>
		</div>
	</div>
</main>
