<script setup>
defineProps({
  producto: { type: Object, required: true },
});

const emit = defineEmits(["delete-item"]);
</script>

<template>
  <article
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
    <p class="text-white text-xs">{{ producto.categoria }}</p>
    <button
      class="absolute right-2 w-8 h-8 bg-red-500 rounded flex items-center justify-center hover:bg-red-400 transition ease-in duration-150 text-slate-900"
      @click="$emit('delete-item', producto.id)"
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
</template>
