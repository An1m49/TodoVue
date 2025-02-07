<script setup lang="ts">
//Пропсы
defineProps({
    name: {
        type: String,
        default: 'Noname'
    },
    date: {
        type: String,
        default: null
    }
})
</script>

<template>
    <div class="mb-3">
        <h1 class="text-2xl mb-1">Привет, {{ name }}</h1>
        <p class="text-xs"> {{ date }}</p>
    </div>
</template>

