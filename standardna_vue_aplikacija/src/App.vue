<script setup>
import ToDoBody from './components/ToDoBody.vue';
import ToDoFooter from './components/ToDoFooter.vue';
import ToDoHeader from './components/ToDoHeader.vue';


</script>

<template>
<div class="flex flex-col h-full">
    <ToDoHeader>To-Do Aplikacija</ToDoHeader>
    <div class="grow">
       Body
    </div>
    <ToDoFooter>Luka Catela</ToDoFooter>
</div>
</template>

<style scoped></style>
