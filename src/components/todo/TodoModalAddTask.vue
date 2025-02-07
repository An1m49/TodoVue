<script setup lang="ts">
//Пропсы
defineProps({
    isShowModal: {
        type: Boolean,
        default: false
    }
})

//Модель и имиты
const inputValue = defineModel<string>('value', { default: '' });
const emit = defineEmits(['apply', 'update:isShowModal']);

//Функции
const applyButton = () => emit('apply');
const closeModal = () => emit('update:isShowModal', false);

</script>

<template>
    <div
        class="
              absolute bg-[#0000006e] top-0 bottom-0 left-0 right-0 min-w-screen min-h-screen
              flex justify-center items-center
              "
    >
        <div class="w-[500px] p-6 bg-[#332934] z-10">
            <div class="flex justify-between items-center mb-6">
                <h2 class="text-3xl">Добавление записи</h2>
                <button class="material-icons cursor-pointer" @click="closeModal">cancel</button>
            </div>

            <div class="">
                <div class="flex flex-col mb-6">
                    <span>Введите дело:</span>
                    <input
                        v-model="inputValue"
                        class="border-b-2 py-2 text-xl outline-none"
                        type="text"
                    >
                </div>

                <div class="">
                    <button
                        class="bg-[#7ccf87] w-full p-4 text-2xl text-white"
                        :class="{'bg-[#a7b3e0]': inputValue.length === 0, 'cursor-pointer': inputValue.length >= 1}"
                        :disabled="inputValue.length === 0"
                        @click="applyButton"
                    >
                        Добавить
                    </button>
                </div>
            </div>
        </div>
    </div>
</template>
