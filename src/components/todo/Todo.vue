<script setup lang="ts">
import Search from '@/components/UI/Search.vue';
import TodoGreeting from "@/components/todo/TodoGreeting.vue";
const testClickButton = () => console.log('click');
</script>

<template>
    <div class="bg-[#3e3341] p-4 text-[#efd6f4] w-[500px]">
       <TodoGreeting
           name="Steve"
           date="03.02.2025"
       />

        <Search @click="testClickButton"/>

    </div>
</template>
