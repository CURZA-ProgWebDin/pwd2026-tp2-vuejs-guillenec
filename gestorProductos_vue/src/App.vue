<script setup>
import { ref } from "vue";
import ProductForm from "./components/ProductForm.vue";
import ProductList from "./components/ProductList.vue";
import SearchComponent from "./components/SearchComponent.vue";
const productos = ref([]);

const crearProducto = (producto) => {
  productos.value.push(producto);
};
const deleteItem = (id) => {
  productos.value = productos.value.filter((p) => p.id !== id);
};
</script>

<template>
  <ProductForm @crear-producto="crearProducto" />
  <SearchComponent />
  <ProductList :productos="productos" @delete-item="deleteItem" />
</template>
