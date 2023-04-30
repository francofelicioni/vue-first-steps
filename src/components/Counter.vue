<script setup>
import { ref } from 'vue';
const counter = ref(0)
const increment = () => { counter.value++ }

</script>

<template>
    <div class="flex justify-center items-center gap-3">
       
        <div class="border p-4 bg-red-400 text-black font-bold">
            <button @click="increment">Increment</button>
        </div>

        <h1 class="bg-white text-black p-4 font-bold">
            Counter: {{ counter }}
        </h1>

    </div>
</template>

<style></style>