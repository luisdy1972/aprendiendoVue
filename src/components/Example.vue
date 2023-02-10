<template>
	<h2>Lista de Notas</h2>
	<form class="form-control" @submit.prevent>
		<div class="d-flex flex-row mb-3">
			<input v-model="newNota" />
			<button class="btn btn-primary m-1" @click="addNota">Add</button>
		</div>
		<ul>
			<li v-for="nota in notas" :key="nota.id">
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
<script setup>
import { ref } from "vue"

let id = 0

const notas = ref([
	{ id: id++, text: "Nota 1" },
	{ id: id++, text: "Nota 2" },
])
console.log(notas.value)

const newNota = ref("")

function addNota() {
	notas.value.push(newNota.value)
}

function removerNota(id) {
	notas.value.splice(id)
}
</script>
