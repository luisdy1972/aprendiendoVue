<template>
	<div class="container">
		<h2 class="text-center m-3">Tableros de Interactivo</h2>
		<div class="d-flex justify-content-center gap-2">
			<div
				v-for="board in boards"
				:key="board.boardID"
				class="card shadow board"
			>
				<h3 class="m-3 text-center">{{ board.boardtextTitle }}</h3>
				<ul
					class="container list-group list-group-flush d-flex flex-column justify-content-center mb-2 gap-1"
				>
					<li
						v-for="nota in board.boardNotes"
						class="list-group-item"
					>
						{{ nota }}
					</li>
				</ul>
			</div>
		</div>
	</div>
</template>
<script setup>
import { ref } from "vue"
import { v4 as uuid } from "uuid"
let boards = ref([
	{
		boardID: uuid(),
		boardtextTitle: "Hola titulo 1",
		boardNotes: [{}, "Hola Nota", "Hola Nota detalle", "Hola Nota1"],
		boardEstado: true,
	},
	{
		boardID: uuid(),
		boardtextTitle: "Hola titulo 2",
		boardNotes: ["Hola Nota1", "Hola Nota1", "Hola Nota1"],
		boardEstado: true,
	},
])

console.log(boards.value)
</script>
<style scoped lang="css">
.board {
	min-width: 10rem;
	min-height: 20rem;
}
</style>
