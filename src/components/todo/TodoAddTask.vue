<script setup lang="ts">
//Эмиты
const emit = defineEmits(['add']);

//Функции
const addTask = () => emit('add');
</script>

<template>
    <div class="bg-[#332934] p-4 flex justify-between items-center">
        <h2 class="text-xl">Добавление задачи</h2>

        <button class="material-icons cursor-pointer" @click="addTask">
            add_circle
        </button>
    </div>
</template>
