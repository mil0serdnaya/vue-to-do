<script setup>
  import ToDoListHeader from "./components/ToDoHeader.vue";
  import ToDoList from "./components/ToDoList.vue";
  import AppFooter from "./components/AppFooter.vue";
</script>

<template>
  <section class="to-do-app">
    <ToDoListHeader />
    <ToDoList />
  </section>
  <AppFooter />
</template>

<style lang="scss">
@import "./assets/scss/components/to-do-app.scss";
</style>
