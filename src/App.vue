<script setup>
import AppHeader from "./components/AppHeader.vue";
import ToDoList from "./components/ToDoList.vue";
</script>

<template>
  <main>
    <section>
      <AppHeader/>
      <ToDoList/>
    </section>
  </main>
</template>

<style lang="scss">
@import "./assets/_app.scss";
</style>
