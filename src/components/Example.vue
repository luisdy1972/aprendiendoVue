<script setup>
import { ref } from "vue"
import { v4 as uuid } from "uuid"

const data = ref([])

let textNewNota = ref("")

function addNota(text) {
	let notaExample = {
		id: uuid(),
		text: text,
	}
	data.value.push(notaExample)
	// console.log(data.value)
}

function removerNota(id) {
	data.value = data.value.filter((nota) => nota.id !== id)
	// console.log(data.value.filter((datos) => datos.id !== id))
}
</script>
<template>
	<h2>Lista de Notas</h2>
	<form class="form-control" @submit.prevent>
		<div class="d-flex flex-row mb-3">
			<input v-model="textNewNota" />
			<button class="btn btn-primary m-1" @click="addNota(textNewNota)">
				Add
			</button>
		</div>
		<ul>
			<li v-for="nota in data" :key="nota.id">
				{{ nota.text }}
				<button
					:key="nota.id"
					class="btn btn-danger m-1"
					@click="removerNota(nota.id)"
				>
					X
				</button>
			</li>
		</ul>
	</form>
</template>
