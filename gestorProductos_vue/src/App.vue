<script setup>
import { ref } from "vue";
import FormularioProducros from "./components/FormularioProducros.vue";

const productos = ref([]);

const crearProducto = (producto) => {
  productos.value.push(producto);
};

const listarProductos = (e) => {
  e.preventDefault();

  if (productos.value.length === 0) {
    return alert("no hay productos");
  } else {
    console.log(JSON.stringify(productos.value, null, 2));
  }
};
</script>

<template>
  <FormularioProducros @crear-producto="crearProducto" />
  <button
    class="p-2 rounded-md bg-orange-500 text-white"
    @click="listarProductos"
  >
    ver lista
  </button>
</template>
