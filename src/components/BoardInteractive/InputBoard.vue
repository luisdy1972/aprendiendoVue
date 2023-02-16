<script setup>
import { ref, defineEmits } from "vue";
const nuevaNota = ref("");
const emits = defineEmits(["onNewItem"]);

function handleSubmit() {
  if (nuevaNota !== "") {
    emits("onNewItem", nuevaNota);
    nuevaNota.value = "";
  }
}
</script>
<template lang="">
  <form @submit.prevent="handleSubmit" class="input-group p-2">
    <input
      class="form-control"
      placeholder="Nueva nota"
      v-model="nuevaNota"
      type="text"
    />
    <button class="btn btn-outline-secondary" type="submit">Crear nota</button>
  </form>
</template>
<style scoped lang="css"></style>

<!-- continuar https://youtu.be/aJShMgOmAjE?t=2716 -->
