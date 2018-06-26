<template>
  <div class='has-text-centered todo-form'>
    <button class='button add' v-on:click="openForm" v-show="!isCreating">
      <i class='fa fa-plus-square'></i>
    </button>
    <div class='card' v-show="isCreating">
      <div class='card-content'>
        <div>
          <div class='field'>
            <label class="label">Title</label>
            <div class="control">
              <input class="input" v-model="titleText" type='text' ref='title' defaultValue="">
            </div>
          </div>
          <div class='field'>
            <label class="label">Project</label>
            <div class="control">
              <input class="input" v-model="projectText" type='text' ref='project' defaultValue="">
            </div>
          </div>
          <div>
            <button class='button is-primary' v-on:click="sendForm()">
              Create
            </button>
            <button class='button is-danger' v-on:click="closeForm">
              Cancel
            </button>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      titleText: '',
      projectText: '',
      isCreating: false,
    };
  },
  methods: {
    openForm() {
      this.isCreating = true;
    },
    closeForm() {
      this.isCreating = false;
    },
    sendForm() {
      if (this.titleText.length > 0 && this.projectText.length > 0) {
        const title = this.titleText;
        const project = this.projectText;
        this.$emit('add-todo', {
          title,
          project,
          done: false,
        });
      }
      this.isCreating = false;
    },
  },
};
</script>
<style>
button.add{
  margin-top: 1rem;
}
.todo-form{
  max-width: 400px;
  margin: 1rem auto 0 auto;
}
</style>
