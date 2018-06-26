<template>
  <div class='card todo'>
    <div class="card-content" v-show="!isEditing">
      <div class='title'>
          {{ todo.title }}
      </div>
      <div class='subtitle'>
          {{ todo.project }}
      </div>
      <div class="level">
      <div class="level-left">
      </div>
        <div class="level-right">
          <span class="level-item" v-on:click="showForm">
            <i class='fa fa-pencil-square-o icon-action'></i>
          </span>
          <span class="level-item" v-on:click="deleteTodo(todo)">
            <i class='fa fa-trash-o icon-action'></i>
          </span>
        </div>
      </div>
    </div>

    <div class="card-content" v-show="isEditing">
      <div>
        <div class='field'>
          <label class="label">Title</label>
          <div class="control">
            <input class="input" type='text' v-model="todo.title" >
          </div>
        </div>
        <div class='field'>
          <label class="label">Project</label>
          <div class="control">
            <input class="input" type='text' v-model="todo.project" >
          </div>
        </div>
        <div>
          <button class='button is-primary is-outlined' v-on:click="hideForm">
            Close X
          </button>
        </div>
      </div>
    </div>
    <div class='button is-success' v-show="!isEditing &&todo.done" disabled>
        Completed
    </div>
    <div class='button is-danger is-outlined' v-show="!isEditing && !todo.done" v-on:click="completeTodo(todo)">
        Pending
    </div>
  </div>
</template>
</template>

<script>
export default {
  props: ['todo'],
  data() {
    return {
      isEditing: false,
    };
  },
  methods: {
    showForm() {
      this.isEditing = true;
    },
    hideForm() {
      this.isEditing = false;
    },
    deleteTodo(todo) {
      this.$emit('delete-todo', todo);
    },
    completeTodo(todo) {
      this.$emit('complete-todo', todo);
    },
  },
};
</script>
<style>
.todo{
  max-width: 400px;
  margin: 0 auto;
}
.icon-action{
  cursor: pointer;
}
</style>
