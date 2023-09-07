<script setup>
  import { ref } from 'vue'

  let toDoTitle = ref('')
  let toDoDescription = ref('')

  const onAddToDo = () => {
    console.log(toDoTitle.value, toDoDescription.value)
  }
</script>

<template>
  <div class="to-do-form">
    <input type="text" 
          class="to-do-input" 
          v-model="toDoTitle" 
          name="title"
          placeholder="What needs to be done?">
    <input type="text" 
           class="to-do-input" 
           v-model="toDoDescription"
           name="description"
           placeholder="Additional description for your todo">
    <button class="orange-btn" @click="onAddToDo" value="add">Add</button>
  </div>
</template>

<style lang="scss">
@import "@/assets/styles/_vars.scss";

.to-do-form {
  padding: 20px;
}

.to-do-input {
  display: block;
  width: 100%;
  outline: none;
}
</style>