<script setup>
import { computed, ref } from "vue";
import ProductForm from "./components/ProductForm.vue";
import ProductList from "./components/ProductList.vue";
import FilterProducts from "./components/FilterProducts.vue";
const productos = ref([]);
const filtroCategoria = ref("todas");

const crearProducto = (producto) => {
  productos.value.push(producto);
};

const deleteItem = (id) => {
  productos.value = productos.value.filter((p) => p.id !== id);
};

const productosFiltrados = computed(() => {
  if (filtroCategoria.value === "todas") return productos.value;
  return productos.value.filter((p) => p.categoria === filtroCategoria.value);
});
</script>

<template>
  <ProductForm @crear-producto="crearProducto" />
  <FilterProducts v-model="filtroCategoria" />
  <ProductList :productos="productosFiltrados" @delete-item="deleteItem" />
</template>
