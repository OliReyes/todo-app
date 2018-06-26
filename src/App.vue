<template>
    <div class="section">
      <div class="container">
        <todo-list v-bind:todos="todos"></todo-list>
        <create-todo v-on:add-todo="addTodo"></create-todo>
      </div>
    </div>
</template>

<script>
import TodoList from './components/TodoList';
import CreateTodo from './components/CreateTodo';

export default {
  name: 'todo-app',
  components: {
    TodoList,
    CreateTodo,
  },
  // data function avails data to the template
  data() {
    return {
      todos: [{
        title: 'Todo A',
        project: 'Project A',
        done: false,
      }, {
        title: 'Todo B',
        project: 'Project B',
        done: true,
      }, {
        title: 'Todo C',
        project: 'Project C',
        done: false,
      }, {
        title: 'Todo D',
        project: 'Project D',
        done: false,
      }],
    };
  },
  methods: {
    addTodo(newTodo) {
      this.todos.push(newTodo);
    },
  },
};
</script>

<style>
</style>
