<script setup>
import { ref } from 'vue';

const isFormVisible = ref(false);
const newToDo = ref({ title: '', description: '' });

const emit = defineEmits(['addToDo']);

const addNewToDo = () => {
  if (newToDo.value.title.trim()) {
    emit('addToDo', { ...newToDo.value });
    resetForm();
  }
};

const resetForm = () => {
  newToDo.value = { title: '', description: '' };
  isFormVisible.value = false;
};
</script>

<template>
  <header class="to-do-header">
    <div class="to-do-header__top">
      <h1 class="to-do-header__heading">Todo List</h1>
      <button class="btn--orange" @click="isFormVisible = !isFormVisible">
        New
      </button>
    </div>
    <transition name="fade">
      <div v-if="isFormVisible" class="to-do-form">
        <input
          class="to-do-input"
          v-model="newToDo.title"
          type="text"
          placeholder="Title"
          required
        />
        <input
          class="to-do-input"
          v-model="newToDo.description"
          type="text"
          placeholder="Description (optional)"
        />
        <button class="btn--orange" @click="addNewToDo">Add</button>
      </div>
    </transition>
  </header>
</template>

<style lang="scss" scoped>
.to-do-header {
  &__top {
    display: flex;
    justify-content: space-between;
    align-items: center;
    padding: 30px 15px 20px 30px;
  }

  &__heading {
    font-size: 28px;
    font-weight: 700;
  }
}

.to-do-form {
  padding: 20px;
}

.to-do-input {
  display: block;
  width: 100%;
  margin-bottom: 10px;
  padding: 10px;
  border: 1px solid #ddd;
  border-radius: 5px;
  outline: none;
  font-size: 16px;
}

.to-do-input:focus {
  border-color: #4CAF50;
}

/* .btn--orange {
  background-color: #FF8469;
  color: white;
  border: none;
  padding: 10px 15px;
  border-radius: 5px;
  cursor: pointer;
}

.btn--orange:hover {
  background-color: #D95133;
} */

.fade-enter-active, .fade-leave-active {
  transition: opacity 0.3s;
}
.fade-enter, .fade-leave-to {
  opacity: 0;
}
</style>
