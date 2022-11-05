<script setup>
import ToDoListHeader from "./components/ToDoListHeader.vue";
import ToDoList from "./components/ToDoList.vue";
import AppFooter from "./components/AppFooter.vue";
</script>

<template>
  <section class="to-do-list-app">
    <ToDoListHeader />
    <ToDoList />
  </section>
  <AppFooter />
</template>

<style lang="scss">
@import "./assets/scss/components/_to-do-list-app.scss";
</style>
