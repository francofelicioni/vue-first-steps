<script setup>
// defineProps(['title', 'id', 'text', 'fontColor' ])

defineProps({
    title: {
        type: String,
        default: 'No title'
    },
    id: Number,
    text: {
        type: String,
        default: 'No description'
    },
    fontColor: String
})

const emit = defineEmits(['changeFavoriteName'])

</script>


<template>
    <div class="p-3 w-2/4 content-center m-auto">
        <div class="flex flex-col align-center justify-center bg-white rounded">
            <h5 class="text-black text-center text-xl">
                {{ id }} - {{ title }}
            </h5>
            <p :class="`text-${fontColor}-500`" class="text-black text-center text-xl">
                {{ text }}
            </p>
            <button @click="emit('changeFavoriteName', title)" class="bg-blue-500 font-white font-bold">
                Change favorite
            </button>
        </div>
    </div>
</template>

<style></style>