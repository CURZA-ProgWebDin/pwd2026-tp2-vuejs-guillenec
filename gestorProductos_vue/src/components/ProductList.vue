<script setup>
import { ref } from "vue";

const props = defineProps({
  productos: { type: Array, required: true },
});
</script>

<template>
  <div class="product-list">
    <h2>Lista de Productos</h2>
    <ul>
      <li v-for="producto in productos" :key="producto.id">
        {{ producto.nombre }} - ${{ producto.precio }}
      </li>
    </ul>
  </div>
</template>

<style lang=""></style>
