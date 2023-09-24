<script setup>
  import { ref } from 'vue'

  const isFormVisible = ref(false)
  const emit = defineEmits(['addToDo'])

  let toDoTitle = ref('')
  let toDoDescription = ref('')

  const onAddToDo = () => {
    if (!!toDoTitle.value) {
      let newToDo = {
        title: toDoTitle.value.trim(),
        description: toDoDescription.value.trim()
      }
      emit('addToDo', newToDo)
      toDoTitle.value = ''
      toDoDescription.value = ''
      isFormVisible.value = false
    }
  }
</script>

<template>
  <header class="to-do-header">
    <div class="to-do-header__top">
      <h1 class="to-do-header__heading">Todo list</h1>
      <button class="btn--orange" value="new" @click="isFormVisible = !isFormVisible">New</button>
    </div>
    <Transition name="fade">
      <div class="to-do-form" v-show="isFormVisible">
        <input type="text" class="to-do-input" v-model="toDoTitle" placeholder="What needs to be done?">
        <input type="text" class="to-do-input" v-model="toDoDescription" placeholder="Additional description for your todo (optional)">
        <button class="btn--orange" @click="onAddToDo" value="add">Add</button>
      </div>
    </Transition>
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
