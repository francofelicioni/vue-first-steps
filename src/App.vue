<script setup>

import { ref, computed } from 'vue';

const name = 'San Lorenzo'
const counter = ref(0);
const savedNumbers = ref([]);

console.log(savedNumbers.value)

const handleIncrement = () => {
  counter.value++;
}

const handleDecrement = () => {
  counter.value--;
}

const handleReset = () => {
  counter.value = 0;
}

const addNumber = () => {
  savedNumbers.value.push(counter.value)
}

const cleanNumberList = () => { savedNumbers.value.splice(0, savedNumbers.value.length) }

const classCounter = computed(() => {
  if (counter.value > 0) {
    return "positive";
  }
  else if (counter.value < 0) {
    return "negative";
  } else {
    return "zero";
  }
})

const isDisabled = computed(() => {
  // const numSearch = savedNumbers.value.find(num => num === counter.value)
  // return numSearch || numSearch === 0;

  return savedNumbers.value.indexOf(counter.value) !== -1 
  
  
  // if (numSearch === 0) return true;
  // return numSearch;
})

</script>


<template>
  <div class="grid grid-rows-3 gap-4">
    <h1 class="text-lg">Hello {{ name.toUpperCase() }}!</h1>

    <button class="border rounded-sm hover:bg-white hover:text-black" @click="handleIncrement">
      Aumentar
    </button>
    <button class="border rounded-sm hover:bg-white hover:text-black" @click="handleDecrement">
      Disminuir
    </button>
    <button class="border rounded-sm hover:bg-white hover:text-black" @click="handleReset">
      LLevar a cero
    </button>

    <button :disabled=isDisabled class="py-2 border rounded hover:text-black hover:bg-white" @click="addNumber">
      Agregar número
    </button>

    <button class="py-2 border rounded hover:text-black hover:bg-white" @click="cleanNumberList">
      Limpiar lista
    </button>

    <div
      class="bg-white text-lg font-bold text-center py-2 rounded-lg text-black hover:shadow-lg hover:shadow-cyan-500/50">
      <span :class="classCounter">
        {{ counter }}
      </span>
    </div>


    {{ savedNumbers }}

    <div>
      <ul>
        <li v-for="(num, index) in savedNumbers" :key="index">
          {{ num }}
        </li>
      </ul>
    </div>
  </div>
</template>


<style>
h1 {
  color: red;
}

.positive {
  color: green;
}

.negative {
  color: red;
}

.zero {
  color: peru;
}
</style>



