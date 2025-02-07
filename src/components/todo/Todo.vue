<script setup lang="ts">
import { ref, watch, computed } from 'vue';
import type { ITodoList } from "@/types/todo.ts";
import Search from '@/components/UI/Search.vue';
import TodoGreeting from "@/components/todo/TodoGreeting.vue";
import TodoAddTask from "@/components/todo/TodoAddTask.vue";
import TodoModalAddTask from "@/components/todo/TodoModalAddTask.vue";
import TodoCard from "@/components/todo/TodoCard.vue";

//Переменные
const isShowModal = ref<boolean>(false);
const inputValue = ref<string>('');
const checkboxValue = ref<boolean[]>([]);
const todoList = ref<ITodoList[]>([]);
const searchQuery = ref<string>('');

//Функции
const showAddModal = () => isShowModal.value = true;

const creationDateTask = (date = new Date()) => {
    const day: string = String(date.getDate()).padStart(2, '0');
    const month: string = String(date.getMonth() + 1).padStart(2, '0');
    const year: number = date.getFullYear();
    const hour: string = String(date.getHours()).padStart(2, '0');
    const minutes: string = String(date.getMinutes()).padStart(2, '0');
    return `${day}.${month}.${year} ${hour}:${minutes}`;
}

const applyButton = () => {
    todoList.value.push({
        id: todoList.value.length + 1,
        task: inputValue.value,
        date: creationDateTask(),
        isCompleted: false
    })
    console.log('Запись добавлена');
    checkboxValue.value.push(false)
    inputValue.value = '';
    isShowModal.value = false;
}

const updateTodoStatus = (index: number) => todoList.value[index].isCompleted = checkboxValue.value[index];

const filteredTodos = computed(() => {
    if(!searchQuery.value) return [...todoList.value]
    else return todoList.value.filter(item => item.task.toLowerCase().includes(searchQuery.value.toLowerCase()));
})
</script>

<template>
    <div class="bg-[#3e3341] p-4 text-[#efd6f4] w-[500px]">
       <TodoGreeting
           name="Steve"
           :date="creationDateTask()"
       />

        <Search class="mb-6" v-model:search="searchQuery"/>

        <TodoAddTask class="mb-6" @add="showAddModal"/>

        <TodoModalAddTask
            v-if="isShowModal"
            v-model:value="inputValue"
            v-model:is-show-modal="isShowModal"
            @apply="applyButton"
        />

        <div class="flex flex-col gap-2 max-h-[400px] overflow-y-auto">
            <TodoCard
                v-for="(task, index) in filteredTodos"
                :key="task.id"
                :task="task.task"
                :date="task.date"
                @click="updateTodoStatus(index)"
                v-model:value="checkboxValue[index]"
            />
        </div>
    </div>
</template>
