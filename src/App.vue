<script setup>
import counter from "./components/counter.vue"
import foxs from "./components/foxs.vue"
import galeria from "./components/galeria.vue"
import Gpt from "./components/Gpt.vue"
import ListaNotas from "./components/ListaNotas.vue"
</script>

<template>
	<div class="container mt-5">
		<div>
			<Gpt />
		</div>
		<div>
			<ListaNotas />
			<galeria />
			<foxs />
			<counter />
		</div>
	</div>
</template>

<style scoped></style>
