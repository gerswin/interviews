<script>
	// @ts-nocheck
	import Header from '../Header.svelte';
	import { browser } from '$app/environment';
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
	if (browser) {
		const urlParams = new URLSearchParams(window.location.search);
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
				label: 'Centro de Costos',
				type: 'textfield',
				defaultValue: urlParams.get('costCenter'),
				layout: {
					row: 'Row_0wtkqtg',
					columns: null
				},
				id: 'cost_center',
				key: 'cost_center',
				validate: {
					required: true
				}
			},
			{
				label: 'Email del Candidato',
				defaultValue: urlParams.get('candidateEmail'),
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
				label: 'Email del Seleccionador',
				defaultValue: urlParams.get('recuirterEmail'),
				type: 'textfield',
				layout: {
					row: 'Row_0wtkqtg',
					columns: null
				},
				id: 'recuirter_email',
				key: 'recuirter_email',
				validate: {
					required: true
				}
			},
			{
				label: 'Link de Meet',
				type: 'textfield',
				defaultValue: urlParams.get('meetID'),

				layout: {
					row: 'Row_0wtkqtg8',
					columns: null
				},
				id: 'meet_link',
				key: 'meet_link',
				validate: {
					required: true
				}
			},
			{
				label: 'Oferta publicada',
				type: 'textarea',
				class: 'ofert-text',
				layout: {
					row: 'Row_0wtkqtg',
					columns: null
				},
				id: 'ofert-text',
				key: 'ofert-text',
				validate: {
					required: true
				}
			},
			{
				label: 'Fortalezas del Candidato',
				type: 'textarea',
				class: 'ofert-text',
				layout: {
					row: 'Row_1kutxop',
					columns: null
				},
				id: 'candidate-strengths',
				key: 'candidate-strengths'
			},
			{
				label: 'Áreas de mejora',
				type: 'textarea',
				class: 'ofert-text',
				layout: {
					row: 'Row_1kutxop',
					columns: null
				},
				id: 'candidate-weekness',
				key: 'candidate-weekness'
			},
			{
				values: [
					{
						label: '1',
						value: '1'
					},
					{
						label: '2',
						value: '2'
					},
					{
						label: '3',
						value: '3'
					},
					{
						label: '4',
						value: '4'
					},
					{
						label: '5',
						value: '5'
					}
				],
				label: '¿Cumple con el seniority definido en la oferta? (1: Muy poco, 5: Totalmente)',
				type: 'radio',
				layout: {
					row: 'Row_0po1ewt',
					columns: null
				},
				id: 'seniority-meets',
				key: 'seniority-meets',
				validate: {
					required: true
				}
			},
			{
				values: [
					{
						label: '1',
						value: '1'
					},
					{
						label: '2',
						value: '2'
					},
					{
						label: '3',
						value: '3'
					},
					{
						label: '4',
						value: '4'
					},
					{
						label: '5',
						value: '5'
					}
				],
				label: '¿Satisface los requisitos del perfil solicitado? (1: Muy poco, 5: Totalmente)',
				type: 'radio',
				layout: {
					row: 'Row_0kqv013',
					columns: null
				},
				id: 'requirements-satisfied',
				key: 'requirements-satisfied',
				validate: {
					required: true
				}
			},
			{
				values: [
					{
						label: '1',
						value: '1'
					},
					{
						label: '2',
						value: '2'
					},
					{
						label: '3',
						value: '3'
					},
					{
						label: '4',
						value: '4'
					},
					{
						label: '5',
						value: '5'
					}
				],
				label: '¿Cumple tecnicamente? (1: Muy poco, 5: Totalmente)',
				type: 'radio',
				layout: {
					row: 'Row_0kqv013',
					columns: null
				},
				id: 'tech-satisfied',
				key: 'tech-satisfied',
				validate: {
					required: true
				}
			},
			{
				values: [
					{
						label: '1',
						value: '1'
					},
					{
						label: '2',
						value: '2'
					},
					{
						label: '3',
						value: '3'
					},
					{
						label: '4',
						value: '4'
					},
					{
						label: '5',
						value: '5'
					}
				],
				label: 'Evaluación general (1: Muy Mala, 5: Muy Buena)',
				type: 'radio',
				layout: {
					row: 'Row_0kqv013',
					columns: null
				},
				id: 'overall-satisfied',
				key: 'overall-satisfied',
				validate: {
					required: true
				}
			},
			{
				label: 'Notas adicionales evaluador',
				type: 'textarea',
				class: 'ofert-text',
				layout: {
					row: 'Row_1kutxop',
					columns: null
				},
				id: 'additional-details',
				key: 'additional-details'
			},
			{
				label: 'Aspiracion Salarial',
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
		components.forEach((component) => {
			schema.components.push(component);
		});
	}

	let errors = {};

	const validate = (component, value) => {
		if (component.validate) {
			if (component.validate.required && !value) {
				errors[component.key] = `${component.label} es requerido`;
			} else if (
				component.validate.pattern &&
				!new RegExp(component.validate.pattern).test(value)
			) {
				errors[component.key] = `${component.label} no es válido`;
			} else {
				delete errors[component.key];
			}
		}
	};

	function isRequired(value) {
		return value != null && value !== '';
	}

	const submitForm = (event) => {
		event.preventDefault();
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
			console.log(JSON.stringify(formValues, null, 2));
			console.log('You submit the form.');
		} else {
			console.log('Errors', errors);
		}
	};
</script>

<div class="container" style="padding:20px">
	<Header />
	<form on:submit|preventDefault={submitForm}>
		{#each schema.components as component (component.id)}
			{#if component.type === 'number'}
				<div class="form-group">
					<label for={component.id}><strong>{component.label}</strong></label>
					<input id={component.id} name={component.key} type="number" class="form-control" />
				</div>
			{:else if component.type === 'textfield'}
				<div class="form-group">
					<label for={component.id}><strong>{component.label}</strong></label>

					<input
						id={component.id}
						name={component.key}
						type="text"
						class="form-control"
						value={component.defaultValue ?? ''}
					/>
				</div>
			{:else if component.type === 'textarea'}
				<div class="form-group">
					<label for={component.id}><strong>{component.label}</strong></label>
					<textarea id={component.id} name={component.key} class="form-control {component.class}" />
				</div>
			{:else if component.type === 'datetime'}
				<div class="form-group">
					<label for={component.id}>{component.label}</label>
					<input
						id={component.id}
						name={component.key}
						type="datetime-local"
						class="form-control"
					/>
				</div>
			{:else if component.type === 'select'}
				<div class="form-group">
					<label for={component.id}>{component.label}</label>
					<select id={component.id} name={component.key} class="form-control">
						{#each component.values as value (value.value)}
							<option value={value.value}>{value.label}</option>
						{/each}
					</select>
				</div>
			{:else if component.type === 'radio'}
				<div class="form-group">
					<label for={component.id}><strong>{component.label}</strong></label>
					{#each component.values as value (value.value)}
						<div class="form-check">
							<input
								class="form-check-input"
								type="radio"
								id={value.value}
								name={component.key}
								value={value.value}
							/>
							<label class="form-check-label" for={value.value}>{value.label}</label>
						</div>
					{/each}
				</div>
			{:else if component.type === 'checkbox'}
				<div class="form-check">
					<input class="form-check-input" id={component.id} name={component.key} type="checkbox" />
					<label class="form-check-label" for={component.id}>{component.label}</label>
				</div>
			{:else if component.type === 'checklist'}
				<div class="form-group">
					<label for={component.id}><strong>{component.label}</strong></label>
					{#each component.values as value (value.value)}
						<div class="form-check">
							<input
								class="form-check-input"
								type="checkbox"
								id={value.value}
								name={component.key}
								value={value.value}
							/>
							<label class="form-check-label" for={value.value}>{value.label}</label>
						</div>
					{/each}
				</div>
			{:else if component.type === 'button'}
				<button id={component.id} name={component.key} type="submit" class="btn btn-primary"
					>{component.label}</button
				>
			{/if}
		{/each}
	</form>
</div>

<style>
	.ofert-text {
		height: 200px;
	}
	.form-label {
		font-size: 20px;
		font-weight: bold;
	}
</style>
