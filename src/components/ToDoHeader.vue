<script setup>
import { ref } from 'vue';
const isFormVisible = ref(false);
const newToDo = ref({ title: '', description: '' });

const emit = defineEmits(['addToDo']);

const addNewToDo = () => {
  if (newToDo.value.title.trim()) {
    emit('addToDo', { ...newToDo.value });
    newToDo.value = { title: '', description: '' };
    isFormVisible.value = false;
  }
};
</script>

<template>
  <header class="to-do-header">
    <div class="to-do-header__top">
      <h1 class="to-do-header__heading">Todo List</h1>
      <button class="btn--orange" value="new" @click="isFormVisible = !isFormVisible">New</button>
    </div>
    <transition name="fade">
      <div v-if="isFormVisible" class="to-do-form">
        <input class="to-do-input" v-model="newToDo.title" type="text" placeholder="Title" />
        <input class="to-do-input" v-model="newToDo.description" type="text" placeholder="Description (optional)" />
        <button class="btn--orange" value="add" @click="addNewToDo">Add</button>
      </div>
    </transition>
  </header>
</template>

<style lang="scss">
.to-do-header {
  &__top {
    width: 100%;
    display: flex;
    justify-content: space-between;
    align-items: center;
    padding: 30px 15px 20px 30px;
  }

  &__heading {
    font-weight: 700;
    font-size: 28px;
  }
}

.to-do-form {
  padding: 20px;
}

.to-do-input {
  display: block;
  width: 100%;
  outline: none;
}
</style>
