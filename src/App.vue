<script setup>
import { ref, computed } from "vue";

const name = "Mundo";
// const styleColor = "color: blue";

// const activo = true;

// const arrayFrutas = ["🍎", "🍌", "🍉", "🍓", "🍒"];

// const arrayFrutas = [
//   {
//     name: "Manzana",
//     price: "$1.00",
//     description: "Una manzana",
//   },
//   {
//     name: "Pera",
//     price: "$2.00",
//     description: "Una pera",
//   },
//   {
//     name: "Naranja",
//     price: "$3.00",
//     description: "Una naranja",
//   },
// ];

// const objetoFruta = {
//   name: "Manzana",
//   price: "$1.00",
//   description: "Una manzana",
//   id: 1,
// };

// const arrayFrutas = [
//   {
//     name: "Manzana",
//     price: "$1.00",
//     description: "Una manzana",
//     stock: 0,
//   },
//   {
//     name: "Pera",
//     price: "$2.00",
//     description: "Una pera",
//     stock: 10,
//   },
//   {
//     name: "Naranja",
//     price: "$3.00",
//     description: "Una naranja",
//     stock: 20,
//   },
// ];

// Funcion para manejar eventos (Metodos)
// const handleClick = (texto) => {
//   console.log(texto);
// };

const counter = ref(0);
const array = ref([]);

const incremento = () => counter.value++;

const decremento = () => counter.value--;

const reseteo = () => (counter.value = 0);

const add = () => {
  array.value.push(counter.value);
};

const stateCounter = computed(() => {
  if (counter.value === 0) {
    return "text-white font-bold text-6xl";
  }
  if (counter.value > 0) {
    return "text-green-600 font-bold text-6xl";
  }
  if (counter.value < 0) {
    return "text-red-600 font-bold text-6xl";
  }
});

const bloqueado = computed(() => {
  const numSearch = array.value.find((num) => num === counter.value);
  if (numSearch === 0) return true;
  return numSearch ? true : false;
});

// const prueba = anfn (atajo para funcion flecha)
</script>

<template>

  <!-- <h1>Hola {{ name }}</h1> -->
  <!-- <h1>Adios {{ name }}</h1> -->

  <!-- Estilos en linea -->
  <!-- <h2 :style="styleColor">Adios {{ name }}</h2> -->

  <!-- Manejo de condicionales -->
  <!-- <h2>{{ activo ? "Estoy activo" : "Estoy inactivo" }}</h2>

  <h2 v-if="activo">Estoy activo</h2>

  <p v-if="!activo">Estoy inactivo</p>

  <p v-show="activo">Estoy activo v-show</p> -->

  <!-- Iteracion arrays de string-->
  <!-- <ul>
    <li
    v-for="(fruta, index) in arrayFrutas"
    :key="index"
    >{{ index }} - {{ fruta }}</li>
  </ul> -->

  <!-- Iteracion arrays de objetos -->
  <!-- <ul>
    <li v-for="(fruta, index) in arrayFrutas" :key="index">
      {{ fruta.name }} - {{ fruta.price }} -
      {{ fruta.description }}
    </li>
  </ul> -->

  <!-- Iteracion objetos -->
  <!-- <ul>
    <li v-for="(value, propiedad, index) in objetoFruta" :key="index"> {{ index }} - {{ propiedad }} : {{ value }}</li>
  </ul> -->

  <!-- Iteracion arrays de objetos (con condicional) -->
  <!-- <template v-for="(fruta, index) in arrayFrutas" :key="index">
    <li v-if="fruta.stock > 0">{{ fruta.name }} - {{ fruta.price }}</li>
  </template> -->

  <!-- Eventos con el mouse -->

  <!-- Sintaxis original -->
  <!-- <button v-on:click="handleClick">Click</button> -->

  <!-- Sintaxis abreviada -->
  <!-- <button @click="handleClick">Click</button> -->

  <!-- Pasar parametros -->
  <!-- <button @click="handleClick('Developer Designer Frontend')">Click</button> -->
  <div class="bg-gray-800 text-white w-full h-screen flex flex-col items-center gap-5">
    <h1 class="text-4xl pt-10">App con Vue Js.</h1>
    <div class="flex gap-10 items-center text-lg p-10">
      <button class="bg-red-500 px-6 py-1 rounded-full text-black font-bold text-xl" @click="decremento">-</button>
      <h2 :class="stateCounter">{{ counter }}</h2>
      <button class="bg-green-500 px-6 py-1 rounded-full text-black font-bold text-xl" @click="incremento">+</button>
    </div>
    <div>
      <ul class="text-xl font-semibold flex gap-4">
        <li class="rounded-full border p-2" v-for="(num, index) in array" :key="index"> {{ num }}</li>
      </ul>
    </div>
    <div class="flex gap-10">
      <button class="text-red-600 text-2xl font-semibold" @click="reseteo">Reset</button>
      <button class="text-green-600 text-2xl font-semibold" @click="add" :disabled="bloqueado">Add</button>
    </div>
  </div>
</template>

