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

const cantidadTotalProductos = computed(() => {
  return productosFiltrados.value.reduce(
    (acumulado, producto) => acumulado + producto.stock,
    0,
  );
});

const valorTotalInventario = computed(() => {
  return productosFiltrados.value.reduce(
    (acumulado, producto) => acumulado + producto.precio * producto.stock,
    0,
  );
});
</script>

<template>
  <ProductForm @crear-producto="crearProducto" />
  <FilterProducts v-model="filtroCategoria" />
  <section class="w-full max-w-3xl mx-auto mt-6 px-4">
    <div class="bg-slate-100 border border-slate-300 rounded p-4 flex gap-6">
      <p class="text-slate-700">
        Cantidad total:
        <span class="font-bold">{{ cantidadTotalProductos }}</span>
      </p>
      <p class="text-slate-700">
        Valor inventario:
        <span class="font-bold">${{ valorTotalInventario }}</span>
      </p>
    </div>
  </section>
  <ProductList :productos="productosFiltrados" @delete-item="deleteItem" />
</template>
