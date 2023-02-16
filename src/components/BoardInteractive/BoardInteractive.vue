<script setup>
import { ref, reactive } from "vue";
import { v4 as uuid } from "uuid";
import inputBoard from "./inputBoard.vue";
const boards = reactive([
  {
    id: uuid(),
    title: "tablero 1",
    items: [
      {
        id: uuid(),
        title: "Tarea",
      },
      {
        id: uuid(),
        title: "Tarea nueva",
      },
    ],
  },
  {
    id: uuid(),
    title: "tablero 2",
    items: [
      {
        id: uuid(),
        title: "Tarea2",
      },
      {
        id: uuid(),
        title: "Tarea nueva2",
      },
    ],
  },
]);
</script>
<template>
  <div class="container">
    <div class="text-center m-3">
      <h5>Agregar Tablero</h5>
      <div>
        <form class="input-group">
          <input class="form-control" placeholder="Nuevo tablero" type="text" />
          <button class="btn btn-outline-secondary" type="sutmit">
            Crear Tablero
          </button>
        </form>
      </div>
    </div>

    <h2 class="text-center m-3">Tableros de Interactivo</h2>
    <div class="d-flex justify-content-center gap-5">
      <div
        v-for="(el, index) in boards"
        :key="boards.id"
        class="d-flex justify-content-center"
      >
        <div class="card shadow board">
          <h3 class="m-3 text-center">{{ el.title }}</h3>
          <inputBoard />
          <ul
            class="container list-group list-group-flush d-flex flex-column justify-content-center mb-2 gap-1"
          >
            <li
              v-for="(nota, index) in el.items"
              :key="nota.id"
              class="list-group-item tarea-item"
            >
              {{ nota.title }}
            </li>
          </ul>
        </div>
      </div>
    </div>
  </div>
</template>
<style scoped lang="css">
.board {
  background-color: aliceblue;
  min-width: 10rem;
  min-height: 20rem;
}
.tarea-item {
  font-style: italic;
  background-color: transparent;
}
</style>
