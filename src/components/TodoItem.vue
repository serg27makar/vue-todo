<template>
  <li>
    <span v-bind:class="{done: todo.completed}">
      <input type="checkbox"
             v-model="todo.completed"
             @change="todo.completed = !todo.completed"
      >
      <strong>{{index + 1}}</strong>
      {{todo.title | upercase}}
    </span>
    <button class="rm"
            @click="$emit('remove-todo', todo.id)"
    >&times;</button>
  </li>
</template>

<script>
export default {
  props: {
    todo: {
      type: Object,
      required: true
    },
    index: Number
  },
  filters: {
    upercase(value) {
      return value.toUpperCase();
    }
  },
  name: "TodoItem"
}
</script>

<style scoped>
  li {
    border: 1px solid #ccc;
    display: flex;
    justify-content: space-between;
    padding: .5rem;
    margin-bottom: 1rem;
  }
  .rm {
    background: red;
    color: #fff;
    border-radius: 50%;
    font-weight: bold;
  }
  input {
    margin-right: 1rem;
  }
  .done {
    text-decoration: line-through;
  }
</style>