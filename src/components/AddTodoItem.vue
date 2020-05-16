<template>
    <div class="form-box">
        <form class="add-todo-form" @submit="addTodo">
            <input type="text" name="title" placeholder="Add todo..." class="todo-input inp" v-model="title">
            <input type="submit" value="+" class="submit btn inpt" >
        </form>
    </div>
</template>

<script>
import { v4 } from 'uuid';

export default {
    name: "AddTodoItem",
    data() {
        return {
            title: ''
        }
    },
    methods: {
        addTodo(e) {
            e.preventDefault();
            
            console.log(this.title)
            const newTodo = {
                id: v4(),
                title: this.title,
                completed: false
            }

            // Send to parent
            this.$emit('add-todo', newTodo);
            this.title = ''
        }
    }
}
</script>

<style scoped>
    .form-box {
        padding: 15px;
    }
    .add-todo-form {
        display: flex;
    }
    
    .todo-input-form {
        width: 90%;
    }

    .submit {
        width: 10%;
        font-weight: bolder;
        font-size: 20px;
    }
</style>