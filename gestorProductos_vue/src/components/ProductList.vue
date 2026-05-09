<script setup>
import ProductItem from "./ProductItem.vue";

defineProps({
  productos: { type: Array, required: true },
});
</script>

<template>
  <div class="product-list w-full mt-10">
    <h2 class="text-2xl font-bold capitalize text-center">
      Lista de Productos
    </h2>
    <section
      class="w-full p-5 flex flex-wrap justify-center items-center gap-3"
    >
      <ProductItem
        v-for="producto in productos"
        :key="producto.id"
        :producto="producto"
      />
    </section>
  </div>
</template>

<style lang=""></style>
