<script setup lang="ts">

const emit = defineEmits(['click']);

const clickButton = () => emit('click');
</script>

<template>
    <div class="bg-[#332934] flex justify-between gap-4">
        <input
            class="w-full p-3 outline-none"
            type="text"
            placeholder="Search your lists">
        <button
            class="
                flex justify-center items-center
                bg-red-600 w-[50px] z-10 cursor-pointer
                duration-300 transition-all
                hover:bg-red-300 hover:text-black
            "
            @click="clickButton"
        >
            <span class="material-icons">search</span>
        </button>
    </div>
</template>
