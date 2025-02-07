<script setup lang="ts">
//Пропсы
defineProps({
    task: {
        type: String,
        default: null
    },
    date: {
        type: String,
        default: null
    },
})

//Модель и эмиты
const checkboxValue = defineModel('value');
const emit = defineEmits(['click']);

//Функции
const clickCheckbox = () => emit('click')
</script>

<template>
    <div class="bg-[#29222a] p-4 flex justify-between items-center">
        <div class="">
            <h2
                class="text-xl mb-2"
                :class="[{'text-red-600 line-through': checkboxValue}]"
            >
                {{ task }}
            </h2>
            <p class="text-sm">{{ date }}</p>
        </div>

        <div class="">
            <input
                v-model="checkboxValue"
                class="w-6 h-6"
                type="checkbox"
                @change="clickCheckbox"
            >
        </div>
    </div>
</template>

