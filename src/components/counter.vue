<script setup>
import { ref, computed } from "vue"
const contador = ref(0)

const incremento = () => {
	contador.value++
}
const decremento = () => {
	contador.value--
}
const resetar = () => {
	contador.value = 0
}

const claseContador = computed(() => {
	if (contador.value < 0) {
		return "rojo"
	}
	if (contador.value > 0) {
		return "verde"
	} else {
		return "azul"
	}
})

const ListaNumeros = ref([])

const claseBotonGuardar = computed(() => {
	let nuevoNumero = contador.value
	if (ListaNumeros.value.indexOf(nuevoNumero) !== -1) {
		console.log(ListaNumeros.value.indexOf(nuevoNumero))
		return true
	} else {
		return false
	}
})

function agregarNumero() {
	ListaNumeros.value.push(contador.value)
}
</script>
<template>
	<div class="container">
		<div class="d-flex justify-content-center">
			<h1 :class="claseContador">Contador: {{ contador }}</h1>
			<div>
				<button class="m-1 btn btn-success" @click="incremento">
					+
				</button>
				<button class="m-1 btn btn-danger" @click="decremento">
					-
				</button>
				<button class="m-1 btn btn-secondary" @click="resetar">
					0
				</button>
				<button
					:disabled="claseBotonGuardar"
					class="m-1 btn btn-primary"
					@click="agregarNumero"
				>
					Guardar
				</button>
			</div>
		</div>
		<div class="d-flex justify-content-center">
			<h2>Lista de numeros favoritos</h2>
		</div>
		<ul class="text-center">
			<div v-for="item in ListaNumeros">{{ item }}</div>
		</ul>
	</div>
</template>

<style>
.azul {
	color: blue;
}
.rojo {
	color: red;
}
.verde {
	color: green;
}
</style>
