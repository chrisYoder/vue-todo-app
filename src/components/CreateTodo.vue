<template>
  <div class="ui basic content center aligned segment">
    <button class="ui basic button icon" @click="openForm" v-show="!isCreating">
      <i class="plus icon"></i>
    </button>
    <div class="ui centered card" v-show="isCreating">
      <div class="content">
        <div class="ui form">
          <div class="field">
            <label>Title</label>
            <input type="text" ref="title" v-model="titleText" defaultValue>
          </div>
          <div class="field">
            <label>Project</label>
            <input type="text" ref="project" v-model="projectText" defaultValue>
          </div>
          <div class="ui two button attached buttons">
            <button class="ui basic blue button" @click="sendForm()">Create</button>
            <button class="ui basic red button" @click="closeForm">Cancel</button>
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
      titleText: "",
      projectText: "",
      isCreating: false
    };
  },

  methods: {
    sendForm() {
      if (this.titleText.length > 0 && this.projectText.length > 0) {
        const title = this.titleText;
        const project = this.projectText;
        this.$emit("create-todo", {
          title,
          project,
          done: false
        });
        this.newTodoText = "";
      }

      this.isCreating = false;
    },

    openForm() {
      this.isCreating = true;
    },

    closeForm() {
      this.isCreating = false;
    }
  }
};
</script>

<style>
i {
  font-size: 700;
}
</style>

