<template>
  <div>
    <div class="has-text-centered extra-info">
      <p class="button is-success" disabled>Completed Tasks: {{todos.filter(todo => {return todo.done === true}).length}}</p>
      <p class="button is-danger" disabled>Pending Tasks: {{todos.filter(todo => {return todo.done === false}).length}}</p>
    </div>
    <todo v-on:delete-todo="deleteTodo" v-on:complete-todo="completeTodo" v-for="todo in todos" v-bind:todo="todo"></todo>
  </div>
</template>

<script type = "text/javascript" >
import Todo from './Todo';

export default {
  props: ['todos'],
  components: {
    Todo,
  },
  methods: {
    deleteTodo(todo) {
      const todoIndex = this.todos.indexOf(todo);
      this.todos.splice(todoIndex, 1);
    },
    completeTodo(todo) {
      const todoIndex = this.todos.indexOf(todo);
      this.todos[todoIndex].done = true;
    },
  },
};
</script>
<style>
.extra-info{
  margin-bottom: 1rem;
}
</style>
