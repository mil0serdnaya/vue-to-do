<script setup>
  import ToDoListHeader from './components/ToDoHeader.vue'
  import ToDoList from './components/ToDoList.vue'
  import AppFooter from './components/AppFooter.vue'

  import { ref } from 'vue'

  const toDoItems = ref([])
</script>

<template>
  <section class="to-do-app">
    <ToDoListHeader />
    <ToDoList />
  </section>
  <AppFooter />
</template>

<style lang="scss">
@import "@/assets/styles/_base.scss";

.to-do-app {
  width: 100%;
  max-width: 420px;
  min-height: 540px;
  margin: 0 auto;
  padding-right:  15px;
  background: #252E42;
  box-shadow: 0px 14px 34px rgba(0, 0, 0, 0.25);
  border-radius: 20px 0px 40px;
  position: relative;

  @media (max-width: 768px) { 
    max-width: 390px;
  }

  &::before {
    content: '';
    position: absolute;
    display: block;
    top: -20px;
    width: 395px;
    left: 0;
    height: 68px;
    background: linear-gradient(180deg, #31394D 0%, #091739 100%);
    border-radius: 20px;
    transform: rotate(-2.32deg);
    z-index: -1;

    @media (max-width: 768px) { 
      width: 328px;
      height: 67px;
    }
  }
  
  &::after {
    content: '';
    position: absolute;
    top: -30px;
    width: 342px;
    left: 0;
    height: 86px;
    background: linear-gradient(180deg, #4F5565 0%, #000000 53.65%);
    border-radius: 20px;
    transform: rotate(-4.48deg);
    z-index: -2;
    
    @media (max-width: 768px) { 
      width: 284px;
      height: 85px;
    }
  }
}

</style>
