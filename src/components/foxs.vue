<script setup>
import axios from "axios"
import { onMounted, ref } from "vue"
// fetch("https://randomfox.ca/floof/")
// 	.then((res) => res.json)
// 	.then((data) => {
// 		console.log(data.result)
// 	})
const imagenes = ref()

const buscarIMG = async () => {
	try {
		const respuesta = await axios.get(
			"https://api.thecatapi.com/v1/images/search?limit=10"
		)
		imagenes.value = respuesta.data
	} catch (error) {
		console.error(error)
	}
}
buscarIMG()

// onMounted(() => {

// })
</script>
<template>
	<h3 class="text-center">Gatos API</h3>
	<!-- <div class="container d-flex row text-center">
	    <img
			
			alt="zorro"
			class="col-3 card p-5"
	</div>/-->
	<div class="container">
		<div class="row d-flex justify-content-center">
			<div
				v-for="imagen in imagenes"
				:key="imagen.id"
				class="card p-1 m-1 col-5"
			>
				<img
					:src="imagen.url"
					class="card-img-top imagen-card"
					alt="foto de gato"
				/>
				<div class="card-body">
					<h5 class="card-title">Card title</h5>
					<a href="#" class="btn btn-primary">♥</a>
				</div>
			</div>
		</div>
	</div>
</template>
<style>
.imagen-card {
	height: 20rem;
	object-fit: cover;
}
</style>
