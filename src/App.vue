<script setup>
import ToDoListHeader from "./components/ToDoHeader.vue";
import ToDoList from './components/ToDoList.vue';
import { reactive } from 'vue';

const toDoList = reactive([]);

const addToDo = ({ title, description }) => {
  toDoList.push({
    id: Date.now(),
    title,
    description,
    completed: false,
  });
};

const editToDo = (updatedToDo) => {
  const toDo = toDoList.find(todo => todo.id === updatedToDo.id);
  if (toDo) Object.assign(toDo, updatedToDo);
};

const deleteToDo = (id) => {
  const index = toDoList.findIndex(todo => todo.id === id);
  if (index !== -1) toDoList.splice(index, 1);
};
</script>

<template>
  <section class="to-do-app">
    <ToDoListHeader @add-to-do="addToDo" />
    <ToDoList 
      :to-do-list="toDoList"
      @edit-to-do="editToDo"
      @delete-to-do="deleteToDo"
    />
  </section>
</template>

<style lang="scss">
.to-do-app {
  max-width: 420px;
  min-height: 540px;
  margin: 0 auto;
  padding-right: 15px;
  background: #252E42;
  box-shadow: 0 14px 34px rgba(0, 0, 0, 0.25);
  border-radius: 20px 0 40px;
  position: relative;

  @media (max-width: 768px) {
    max-width: 390px;
  }

  &::before, &::after {
    content: '';
    position: absolute;
    border-radius: 20px;
  }

  &::before {
    top: -20px;
    left: 0;
    width: 395px;
    height: 68px;
    background: linear-gradient(180deg, #31394D 0%, #091739 100%);
    transform: rotate(-2.32deg);
    z-index: -1;

    @media (max-width: 768px) { 
      width: 328px;
      height: 67px;
    }
  }

  &::after {
    top: -30px;
    left: 0;
    width: 342px;
    height: 86px;
    background: linear-gradient(180deg, #4F5565 0%, #000000 54%);
    transform: rotate(-4.48deg);
    z-index: -2;

    @media (max-width: 768px) {
      width: 284px;
      height: 85px;
    }
  }
}
</style>
