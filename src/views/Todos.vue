<template>
  <div>
    <h2>Todo application</h2>
    <router-link to="/">Home</router-link>
    <hr>
    <AddTodo @add-todo="addTodo"/>
    <hr>
    <TodoList
        v-bind:todos="todos"
        @remove-todo="removeTodo"
    />
  </div>
</template>

<script>
import TodoList from '@/components/TodoList'
import AddTodo from "@/components/AddTodo";
export default {
  name: 'todos',
  data() {
    return {
      todos: [
        {id: 1, title: 'todo 1', completed: false},
        {id: 2, title: 'todo 2', completed: false},
        {id: 3, title: 'todo 3', completed: false},
      ]
    }
  },
  components: {
    AddTodo,
    TodoList
  },
  mounted() {
    fetch('https://jsonplaceholder.typicode.com/todos/?_limit=5')
        .then(response => response.json())
        .then(json => this.todos = json)
  },
  methods: {
    removeTodo(id) {
      this.todos = this.todos.filter(t => t.id !== id)
    },
    addTodo(todo) {
      this.todos.push(todo);
    }
  }
}
</script>

<style scoped>

</style>