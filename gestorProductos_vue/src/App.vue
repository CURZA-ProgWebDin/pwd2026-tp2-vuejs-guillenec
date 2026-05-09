<script setup>
import { ref } from "vue";
import ProductForm from "./components/ProductForm.vue";
import ProductList from "./components/ProductList.vue";
const productos = ref([]);

const crearProducto = (producto) => {
  productos.value.push(producto);
};
</script>

<template>
  <ProductForm @crear-producto="crearProducto" />
  <ProductList :productos="productos" />
</template>
