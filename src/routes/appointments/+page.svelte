<script>
	// @ts-nocheck
	import { onMount } from 'svelte';
	import success from '../../successfully.json';

	import { Label, Input, Textarea, Select, Radio, Button, Helper, Skeleton } from 'flowbite-svelte';
	import { Modal } from 'flowbite-svelte';

	let data = null;
	let toggled = false;
	let LottiePlayer;
	let defaultModal = false;

	let components = [
		{
			text: 'Formulario para entrevistas',
			type: 'text',
			layout: {
				row: 'Row_00zxlrj',
				columns: null
			},
			id: 'Field_0mm4bvu'
		},
		{
			label: 'Correo electrónico del seleccionador',
			defaultValue: '',
			type: 'textfield',
			layout: {
				row: 'Row_0wtkqtg',
				columns: null
			},
			id: 'creator_email',
			key: 'creator_email',
			validate: {
				required: true
			}
		},
		{
			label: 'Correo electrónico del candidato',
			defaultValue: '',
			type: 'textfield',
			layout: {
				row: 'Row_0wtkqtg',
				columns: null
			},
			id: 'candidate_email',
			key: 'candidate_email',
			validate: {
				required: true
			}
		},
		{
			label: 'Nombre del candidato',
			defaultValue: '',
			type: 'textfield',
			layout: {
				row: 'Row_0wtkqtg',
				columns: null
			},
			id: 'candidate_name',
			key: 'candidate_name',
			validate: {
				required: true
			}
		},
		{
			label: 'Hoja de vida del candidato',
			defaultValue: '',
			type: 'textfield',
			layout: {
				row: 'Row_0wtkqtg',
				columns: null
			},
			id: 'candidate_cv',
			key: 'candidate_cv',
			validate: {
				required: true
			}
		},
		{
			label: 'Prueba tecnica del candidato',
			defaultValue: '',
			type: 'textfield',
			layout: {
				row: 'Row_0wtkqtg',
				columns: null
			},
			id: 'candidate_test',
			key: 'candidate_test',
			validate: {
				required: false
			}
		},
		{
			label: 'Indique el centro de costos asociado',
			type: 'textfield',
			defaultValue: '',
			layout: {
				row: 'Row_0wtkqtg',
				columns: null
			},
			id: 'cost_centers',
			key: 'cost_centers',
			validate: {
				required: true
			}
		},
		{
			label: 'Enlace de la reunión en Google Meet',
			type: 'textfield',
			defaultValue: '',
			layout: {
				row: 'Row_0wtkqtg8',
				columns: null
			},
			id: 'hangout_link',
			key: 'hangout_link',
			validate: {
				required: true
			}
		},
		{
			label: 'Describa la oferta de empleo publicada',
			type: 'textarea',
			class: 'offer-text',
			layout: {
				row: 'Row_0wtkqtg',
				columns: null
			},
			rows: 10,
			id: 'job_description',
			key: 'job_description',
			validate: {
				required: true
			}
		},
		{
			label: 'Analisis de la oferta de empleo',
			type: 'textarea',
			class: 'offer-text',
			rows: 10,

			layout: {
				row: 'Row_0wtkqtg',
				columns: null
			},
			id: 'analysis',
			key: 'analysis',
			validate: {
				required: false
			}
		},
		{
			label: 'Analisis de la prueba técnica',
			type: 'textarea',
			class: 'offer-text',
			rows: 10,

			layout: {
				row: 'Row_0wtkqtg',
				columns: null
			},
			id: 'test_analysis',
			key: 'test_analysis',
			validate: {
				required: false
			}
		},
		{
			values: [
				{
					label: 'Sí',
					value: 'sí'
				},
				{
					label: 'No',
					value: 'no'
				}
			],
			label: '¿El candidato cumple con los años de experiencia solicitados en la oferta de empleo?',
			type: 'radio',
			layout: {
				row: 'Row_0kqv013',
				columns: null
			},
			id: 'years-experience',
			key: 'years-experience',
			validate: {
				required: true
			}
		},
		{
			label:
				'Describa la experiencia profesional del candidato relacionada con la oferta de empleo',
			type: 'textarea',
			rows: 10,

			layout: {
				row: 'Row_1kutxop',
				columns: null
			},
			id: 'experience-related',
			key: 'experience-related'
		},
		{
			values: [
				{
					label: 'Sí',
					value: 'sí'
				},
				{
					label: 'No',
					value: 'no'
				}
			],
			label: '¿El candidato obtuvo una puntuación superior al 50% en la prueba técnica?',
			type: 'radio',
			layout: {
				row: 'Row_0po1ewt',
				columns: null
			},
			id: 'percentage-test',
			key: 'percentage-test',
			validate: {
				required: true
			}
		},
		{
			values: [
				{
					label: 'Presencial',
					value: 'Presencial'
				},
				{
					label: 'Remota',
					value: 'Remota'
				},
				{
					label: 'Híbrida',
					value: 'Híbrida'
				}
			],
			label: '¿El candidato acepta la modalidad de trabajo ofrecida? Indique cuál',
			type: 'radio',
			layout: {
				row: 'Row_0po1ewt',
				columns: null
			},
			id: 'work-mode',
			key: 'work-mode',
			validate: {
				required: true
			}
		},
		{
			values: [
				{
					label: 'OPS',
					value: 'OPS'
				},
				{
					label: 'Obra Labor',
					value: 'Obra Labor'
				},
				{
					label: 'Indefinido',
					value: 'Indefinido'
				}
			],
			label: 'Tipo de contrato ofrecido',
			type: 'radio',
			layout: {
				row: 'Row_0po1ewt',
				columns: null
			},
			id: 'contract-type-mode',
			key: 'contract-type-mode',
			validate: {
				required: true
			}
		},
		{
			label: 'Indique la aspiración salarial del candidato',
			type: 'textfield',
			layout: {
				row: 'Row_0ttqwoz',
				columns: null
			},
			id: 'salary',
			key: 'salary',
			validate: {
				pattern: '^[0-9]*$',
				required: true
			}
		},
		{
			values: [
				{
					label: 'Sí',
					value: 'sí'
				},
				{
					label: 'No',
					value: 'no'
				}
			],
			label: '¿La aspiración salarial del candidato se encuentra dentro del rango presupuestado?',
			type: 'radio',
			layout: {
				row: 'Row_0kqv013',
				columns: null
			},
			id: 'salary-range',
			key: 'salary-range',
			validate: {
				required: true
			}
		},
		{
			values: [
				{
					label: '1 día',
					value: '1'
				},
				{
					label: '2 días',
					value: '2'
				},
				{
					label: '3 días',
					value: '3'
				},
				{
					label: '4 días',
					value: '4'
				},
				{
					label: '5 días',
					value: '5'
				},
				{
					label: '1 semana',
					value: '7'
				},
				{
					label: '2 semanas',
					value: '14'
				},
				{
					label: 'Más de 2 semanas',
					value: '+14'
				}
			],
			label: '¿Cuántos días se estiman para la vinculación del candidato?',
			type: 'select',
			layout: {
				row: 'Row_1gpflkr',
				columns: null
			},
			id: 'days-link',
			key: 'days-link'
		},
		{
			label: 'Proporcione cualquier detalle adicional relevante',
			type: 'textarea',
			rows: 7,

			layout: {
				row: 'Row_1kutxop',
				columns: null
			},
			id: 'additional-details',
			key: 'additional-details'
		},
		{
			action: 'submit',
			label: 'Guardar',
			type: 'button',
			layout: {
				row: 'Row_1rvn02l',
				columns: null
			},
			id: 'Field_0x9evnp',
			key: 'field_1puwi1j'
		}
	];
	let controlsLayout = [
		'previousFrame',
		'playpause',
		'stop',
		'nextFrame',
		'progress',
		'frame',
		'loop',
		'spacer',
		'background',
		'snapshot',
		'zoom',
		'info'
	];
	let schema = {
		components: [],
		type: 'default',
		id: 'Form_1c6o23q',
		exporter: {
			name: 'form-js (https://demo.bpmn.io)',
			version: '0.13.0'
		},
		schemaVersion: 8
	};
	function parseHTML(html) {
		return html
			.replace(/<br>/g, '\n')
			.replace(/<\/?ul>/g, '')
			.replace(/<li>/g, '\t• ')
			.replace(/<\/li>/g, '\n');
	}
	onMount(async () => {
		const urlParams = new URLSearchParams(window.location.search);
		const module = await import('@lottiefiles/svelte-lottie-player');
		LottiePlayer = module.LottiePlayer;
		const id = urlParams.get('interviewID');
		const response = await fetch(
			`https://rkya5ep6d4.execute-api.us-east-1.amazonaws.com/interview/${id}`
		);
		if (response.ok) {
			data = await response.json();
			for (let i = 0; i < components.length; i++) {
				if (
					components[i].type == 'textfield' ||
					components[i].type == 'textarea' ||
					components[i].type == 'select' ||
					components[i].type == 'radio'
				) {
					schema.components.push({
						...components[i],
						defaultValue: parseHTML(data[components[i].key] || '')
					});
				} else {
					schema.components.push({
						...components[i]
					});
				}
			}
			toggled = true;
		} else {
			console.error('HTTP-Error: ' + response.status);
		}
	});
	let errors = {};

	const validate = (component, value) => {
		if (component.validate) {
			if (component.validate.required && !value) {
				errors[component.key] = `${component.label} es requerido`;
				//alert( `${component.label} es requerido`)
			} else if (
				component.validate.pattern &&
				!new RegExp(component.validate.pattern).test(value)
			) {
				errors[component.key] = `${component.label} no es válido`;
				//alert( `${component.label} no es válido`)
			} else {
				delete errors[component.key];
			}
		}
	};

	const submitForm = (event) => {
		event.preventDefault();
		const urlParams = new URLSearchParams(window.location.search);
		const id = urlParams.get('interviewID');

		const formValues = Object.fromEntries(new FormData(event.target));
		const formData = new FormData(event.target);

		for (let field of formData) {
			const [key, value] = field;
			const component = schema.components.find((component) => component.key === key);

			if (component) {
				validate(component, value);
			}
		}

		if (Object.keys(errors).length === 0) {
			const url = `https://rkya5ep6d4.execute-api.us-east-1.amazonaws.com/interview/${id}`; // La URL de tu servidor a la que realizar la solicitud PUT
			fetch(url, {
				method: 'PUT', // o 'POST'
				headers: {
					'Content-Type': 'application/json'
				},
				body: JSON.stringify(formValues) // convertir los datos del formulario a JSON
			})
				.then((response) => {
					if (!response.ok) {
						throw new Error(`HTTP error! status: ${response.status}`);
					} else {
						defaultModal = true;
					}
					return response.json(); // Esto devuelve una promesa
				})
				.then((json) => {
					console.log(json); // Puedes manejar el JSON resultante aquí
				})
				.catch((e) => {
					console.log('Hubo un problema con la solicitud fetch: ' + e.message);
				});
		} else {
			console.log('Errors', errors);
		}
	};
</script>

<div class="p-5">
	<Modal title="Guardado con exito" bind:open={defaultModal} autoclose>
		<LottiePlayer
			src={success}
			autoplay={true}
			loop={true}
			controls={false}
			renderer="svg"
			background="transparent"
			height={400}
			{controlsLayout}
			width={400}
		/>
		<svelte:fragment slot="footer">
			<Button>Entendido</Button>
		</svelte:fragment>
	</Modal>
	{#if toggled}
		<form on:submit|preventDefault={submitForm}>
			{#each schema.components as component (component.id)}
				{#if component.type === 'number'}
					<div class="mb-4">
						<Label for={component.id} class="block font-semibold">{component.label}</Label>
						<Input
							id={component.id}
							name={component.key}
							type="number"
							class="block w-full border py-2 px-4"
						/>
					</div>
				{:else if component.type === 'textfield'}
					<div class="mb-4">
						<Label for={component.id} class="block font-semibold">{component.label}</Label>
						<Input
							id={component.id}
							name={component.key}
							type="text"
							class="block w-full border py-2 px-4"
							color={errors[component.key] ? 'red' : 'base'}
							bind:value={component.defaultValue}
						/>
						{#if errors[component.key]}
							<Helper class="mt-2" color="red"
								><span class="font-medium">Error!</span> {errors[component.key]}</Helper
							>
						{/if}
					</div>
				{:else if component.type === 'textarea'}
					<div class="mb-4">
						<Label for={component.id} class="block font-semibold">{component.label}</Label>
						<Textarea
							rows={component.rows || 3}
							id={component.id}
							name={component.key}
							color={errors[component.key] ? 'red' : 'base'}
							class="block w-full border py-2 px-4 {component.class}"
							bind:value={component.defaultValue}
						/>
						{#if errors[component.key]}
							<Helper class="mt-2" color="red"
								><span class="font-medium">Error!</span> {errors[component.key]}</Helper
							>
						{/if}
					</div>
				{:else if component.type === 'datetime'}
					<div class="mb-4">
						<Label for={component.id} class="block">{component.label}</Label>
						<Input
							id={component.id}
							name={component.key}
							type="datetime-local"
							class="block w-full border py-2 px-4"
						/>
					</div>
				{:else if component.type === 'select'}
					<div class="mb-4">
						<Label for={component.id} class="block font-semibold">{component.label}</Label>
						<Select
							bind:value={component.defaultValue}
							id={component.id}
							name={component.key}
							class="block w-full border py-2 px-4"
						>
							{#each component.values as value (value.value)}
								<option value={value.value}>{value.label}</option>
							{/each}
						</Select>
						{#if errors[component.key]}
							<Helper class="mt-2" color="red"
								><span class="font-medium">Error!</span> {errors[component.key]}</Helper
							>
						{/if}
					</div>
				{:else if component.type === 'radio'}
					<div class="mb-4">
						<Label for={component.id} class="block font-semibold">{component.label}</Label>
						{#each component.values as value (value.value)}
							<div class="flex items-center">
								<Radio
									bind:group={component.defaultValue}
									class="mr-2"
									type="radio"
									id={value.value}
									name={component.key}
									value={value.value}
								/>
								<Label for={value.value}>{value.label}</Label>
							</div>
						{/each}
						{#if errors[component.key]}
							<Helper class="mt-2" color="red"
								><span class="font-medium">Error!</span> {errors[component.key]}</Helper
							>
						{/if}
					</div>
				{:else if component.type === 'checkbox'}
					<div class="flex items-center">
						<Input class="mr-2" id={component.id} name={component.key} type="checkbox" />
						<Label for={component.id}>{component.label}</Label>
					</div>
				{:else if component.type === 'checklist'}
					<div class="mb-4">
						<Label for={component.id} class="block font-semibold">{component.label}</Label>
						{#each component.values as value (value.value)}
							<div class="flex items-center">
								<Input
									class="mr-2"
									type="checkbox"
									id={value.value}
									name={component.key}
									value={value.value}
								/>
								<Label for={value.value}>{value.label}</Label>
							</div>
						{/each}
					</div>
				{:else if component.type === 'button'}
					<Button id={component.id} name={component.key} type="submit" class="btn btn-blue"
						>{component.label}</Button
					>
				{/if}
			{/each}
		</form>
	{:else if LottiePlayer}
		<Skeleton size="xxl" class="mt-8 mb-2.5" />
	{/if}
</div>

<style>

</style>
