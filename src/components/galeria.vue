<script setup>
import { createClient } from "pexels"
import { ref, computed } from "vue"
let text = ref("")
let numero = ref("")
let query = text.value
const datos = ref()
const client = createClient(
	"NEP4uaonvRAjRYSXpE8B23mDftMGDFRhtr0pHHBP027B4YpbSHknQuJn"
)

function BotonBuscar(query) {
	client.photos.search({ query, per_page: numero.value }).then((photos) => {
		cargarFotos(photos.photos)
	})

	function cargarFotos(fotos) {
		console.log(fotos)
		return (datos.value = fotos)
	}
}
</script>
<template>
	<h2 class="text-center">Galeria de Pexels</h2>
	<div class="container">
		<div class="input-group mb-3">
			<input
				v-model="text"
				type="text"
				class="form-control"
				placeholder="Buscar fotografias"
				aria-label="Buscar fotografias"
				aria-describedby="button-addon2"
			/>
			<input
				v-model="numero"
				type="number"
				class="form-control"
				placeholder="Buscar fotografias"
				aria-label="Buscar fotografias"
				aria-describedby="button-addon2"
			/>
			<button
				class="btn btn-outline-secondary"
				type="button"
				id="button-addon2"
				@click="BotonBuscar(text)"
			>
				Buscar
			</button>
		</div>
		<div class="row d-flex justify-content-center">
			<div
				v-for="foto in datos"
				:key="foto.id"
				class="card p-1 m-1 col-5"
			>
				<img
					:src="foto.src.portrait"
					class="card-img-top imagen-card"
					alt="foto de gato"
				/>
				<div class="card-body">
					<h5 class="card-title">{{ foto.alt }}</h5>
					<a href="#" class="btn btn-primary">♥</a>
				</div>
			</div>
		</div>
	</div>
</template>

<style></style>
