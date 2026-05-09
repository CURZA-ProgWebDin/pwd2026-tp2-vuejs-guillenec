<script setup>
defineProps({
  modelValue: { type: String, required: true },
});

const emit = defineEmits(["update:modelValue"]);

const actualizarFiltro = (event) => {
  emit("update:modelValue", event.target.value);
};
</script>

<template>
  <section class="w-full flex justify-center my-6">
    <div class="w-full max-w-md flex flex-col gap-2">
      <label for="filtro-categoria" class="font-semibold text-slate-700">
        Filtrar por categoria
      </label>
      <select
        id="filtro-categoria"
        :value="modelValue"
        @change="actualizarFiltro"
        class="p-2 border border-slate-300 rounded"
      >
        <option value="todas">Todas</option>
        <option value="electronica">Electronica</option>
        <option value="ropa">Ropa</option>
        <option value="alimentos">Alimentos</option>
      </select>
    </div>
  </section>
</template>
