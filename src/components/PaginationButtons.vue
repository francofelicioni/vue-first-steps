<script setup>

defineProps(['start' ,'end', 'postsLength'])

const emit = defineEmits(['prev', 'next'])
</script>

<template>
    <div class="flex p-5 justify-center">
        <button 
            @click="emit('prev')"
            type="button"
            :disabled = "start === 0"
            class="border px-4 py-2 bg-white text-black font-bold rounded hover:bg-black hover:text-white">
            Previous
        </button>
        <button 
            @click="emit('next')"
            type="button"
            :disabled = "end >= postsLength"
            class="border px-4 py-2 bg-white text-black font-bold rounded hover:bg-black hover:text-white">
            Next
        </button>
    </div>
</template>