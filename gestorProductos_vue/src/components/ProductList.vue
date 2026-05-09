<script setup>
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
      <article
        v-for="producto in productos"
        :key="producto.id"
        class="relative w-50 p-2 rounded h-80 bg-slate-700 flex flex-col gap-1"
      >
        <div class="full h-50 bg-slate-600" />
        <h2 class="text-lg font-semibold text-orange-400">
          {{ producto.nombre }}
        </h2>
        <div class="flex justify-between items-center">
          <p class="font-bold text-white">${{ producto.precio }}</p>
          <p class="text-white">Stock: {{ producto.stock }}</p>
        </div>
        <button
          class="absolute right-2 w-8 h-8 bg-red-500 rounded flex items-center justify-center hover:bg-red-400 transition ease-in duration-150 text-slate-900"
        >
          <svg
            xmlns="http://www.w3.org/2000/svg"
            width="20"
            height="20"
            viewBox="0 0 24 24"
            fill="none"
            stroke="currentColor"
            stroke-width="2"
            stroke-linecap="round"
            stroke-linejoin="round"
            class="lucide lucide-trash-icon lucide-trash"
          >
            <path d="M19 6v14a2 2 0 0 1-2 2H7a2 2 0 0 1-2-2V6" />
            <path d="M3 6h18" />
            <path d="M8 6V4a2 2 0 0 1 2-2h4a2 2 0 0 1 2 2v2" />
          </svg>
        </button>
      </article>
    </section>
  </div>
</template>

<style lang=""></style>
