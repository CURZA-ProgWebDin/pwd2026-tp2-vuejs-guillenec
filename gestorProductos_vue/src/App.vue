<script setup>
import { ref } from "vue";
import ProductForm from "./components/ProductForm.vue";
import ProductList from "./components/ProductList.vue";
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
  <ProductForm @crear-producto="crearProducto" />
  <button
    class="p-2 rounded-md bg-orange-500 text-white"
    @click="listarProductos"
  >
    ver lista
  </button>
  <ProductList :productos="productos" />
</template>
