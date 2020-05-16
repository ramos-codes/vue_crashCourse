<template>
  <div id="app">
    <Header />
    <AddTodoItem v-on:add-todo="addTodo"/>
    <Todos v-bind:todos="todos" v-on:del-todo="deleteTodo"/>
  </div>
</template>

<script>
import Todos from './components/Todos';
import Header from './components/layout/Header';
import AddTodoItem from './components/AddTodoItem';

const todosArr = [
  {
    id: 1,
    title: 'Todo 1',
    completed: false
  },
  {
    id: 2,
    title: 'Todo 2',
    completed: false
  },
  {
    id: 3,
    title: 'Todo 3',
    completed: false
  }
]

export default {
  name: 'App',
  components: {
    Todos,
    Header,
    AddTodoItem
  },
  data() {
    return {
      todos: todosArr
    }
  },
  methods: {
    deleteTodo(id) {
      this.todos = this.todos.filter(todo => todo.id !== id);
    },
    addTodo(newTodo) {
      this.todos = [...this.todos, newTodo]
    }
  }
}
</script>

<style>
* {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}

body {
  font-family: Arial, Helvetica, sans-serif;
  line-height: 1.4;
}
</style>
