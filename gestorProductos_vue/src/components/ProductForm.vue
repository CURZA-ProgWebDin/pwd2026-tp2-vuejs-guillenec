<script setup>
import { ref } from "vue";
const nombre = ref("");
const precio = ref("");
const stock = ref("");
const categoria = ref("electronica");
const errores = ref({
  error_nombre: "",
  error_precio: "",
  error_stock: "",
  error_categoria: "",
});

const emit = defineEmits(["crear-producto"]);

const listaCategorias = [
  { id: 1, nombre: "electronica" },
  { id: 2, nombre: "ropa" },
  { id: 3, nombre: "alimentos" },
];

const validateForm = () => {
  errores.value.error_nombre = "";
  errores.value.error_precio = "";
  errores.value.error_stock = "";
  errores.value.error_categoria = "";

  let esValido = true;

  if (!nombre.value.trim()) {
    errores.value.error_nombre = "El nombre es obligatorio";
    esValido = false;
  }

  if (precio.value === "" || Number.isNaN(precio.value)) {
    errores.value.error_precio = "El precio es obligatorio";
    esValido = false;
  } else if (precio.value <= 0) {
    errores.value.error_precio = "El precio debe ser mayor que 0";
    esValido = false;
  }

  if (stock.value === "" || Number.isNaN(stock.value)) {
    errores.value.error_stock = "El stock es obligatorio";
    esValido = false;
  } else if (stock.value < 0) {
    errores.value.error_stock = "El stock no puede ser negativo";
    esValido = false;
  }

  if (!categoria.value) {
    errores.value.error_categoria = "La categoria es obligatoria";
    esValido = false;
  }

  return esValido;
};

const enviar = () => {
  if (!validateForm()) return;
  const objeto = {
    id: Date.now(),
    nombre: nombre.value,
    precio: precio.value,
    stock: stock.value,
    categoria: categoria.value,
  };
  console.log({ objeto });
  emit("crear-producto", objeto);
};
</script>

<template>
  <section
    class="container mx-auto w-full flex flex-col justify-center items-center p-2 bg-white gap-5 py-5"
  >
    <h1 class="text-2xl font-bold">Formulario de Productos</h1>
    <form
      @submit.prevent="enviar"
      class="w-full max-w-md flex flex-col gap-2 p-4 bg-white rounded-2xl shadow-lg shadow-slate-800"
    >
      <label for="nombre" class="font-bold">Nombre del Producto</label>
      <input
        type="text"
        id="nombre"
        v-model="nombre"
        class="p-2 border border-gray-300 rounded"
      />
      <span v-if="errores.error_nombre" class="text-red-500">{{
        errores.error_nombre
      }}</span>
      <label for="precio" class="font-bold">Precio</label>
      <input
        type="number"
        id="precio"
        v-model.number="precio"
        class="p-2 border border-gray-300 rounded"
      />
      <span v-if="errores.error_precio" class="text-red-500">{{
        errores.error_precio
      }}</span>
      <label for="stock" class="font-bold">Stock</label>
      <input
        type="number"
        id="stock"
        v-model.number="stock"
        class="p-2 border border-gray-300 rounded"
      />
      <span v-if="errores.error_stock" class="text-red-500">{{
        errores.error_stock
      }}</span>
      <label for="categoria">Categoria</label>
      <select
        name="categoria"
        id="categoria"
        v-model="categoria"
        class="p-2 bg-slate-700 text-white rounded"
      >
        <option value="electronica">Electronica</option>
        <option value="ropa">Ropa</option>
        <option value="alimentos">Alimentos</option>
      </select>
      <span v-if="errores.error_categoria" class="text-red-500">{{
        errores.error_categoria
      }}</span>

      <button
        type="submit"
        class="p-2 bg-slate-500 text-white rounded hover:bg-slate-700"
      >
        Enviar
      </button>
    </form>
  </section>
</template>

<style lang=""></style>
