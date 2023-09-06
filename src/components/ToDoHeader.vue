<script setup>
  import ToDoForm from './ToDoForm.vue'

  import { ref } from 'vue'

  const isFormVisible = ref(false)
</script>

<template>
  <header class="to-do-header">
    <div class="to-do-header__top">
      <h1 class="to-do-header__heading">Todo list</h1>
      <button class="orange-btn" value="new" @click="isFormVisible = !isFormVisible">New</button>
    </div>
    <Transition name="fade">
      <ToDoForm v-show="isFormVisible"/>
    </Transition>
  </header>
</template>

<style lang="scss">
@import "@/assets/styles/_vars.scss";

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
</style>
