<template>
    <div class="todos-main-container">
        <div v-for="todo in todos" v-bind:key="todo.id" class="todo-box">
            <TodoItem v-bind:todo="todo" v-on:del-todo="$emit('del-todo', todo.id)"/> 
        </div>
    </div>
</template>

<script>
import TodoItem from './TodoItem';

export default {
    name: "Todos",
    components: {
        TodoItem
    },
    props: ["todos"]
}
</script>

<style scoped>
    .todos-main-container {
        padding: 15px;
    }

    .todo-box {
        margin: 10px auto;
    }
</style>