<template>
  <div id="app">
    <AddTodoItem v-on:add-todo="addTodo"/>
    <Todos v-bind:todos="todos" v-on:del-todo="deleteTodo"/>
  </div>
</template>

<script>
import Todos from '../components/Todos';
import AddTodoItem from '../components/AddTodoItem';
import todosJson from '../apis/todosJson';

export default {
  name: 'Home',
  components: {
    Todos,
    AddTodoItem
  },
  data() {
    return {
      todos: []
    }
  },
  async mounted() {
    const response = await todosJson.get('todos?_limit=10');

    this.todos = response.data
  },
  methods: {
    deleteTodo(id) {
      todosJson.delete(`todos/${id}`)
        .then(res => res.status(201).json({ data: res.data }))
        .catch(err => console.error(err));
      this.todos = this.todos.filter(todo => todo.id !== id);
    },
    addTodo(newTodo) {
      const { title, completed } = newTodo
      todosJson.post('todos', {
        title,
        completed
      })
      .then(res => this.todos = [...this.todos, res.data])
      .catch(err => console.log(err));
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
