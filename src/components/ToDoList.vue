<script setup>
import ToDoItem from './ToDoItem.vue';
defineProps(['toDoList']);
const emit = defineEmits(['editToDo', 'deleteToDo']);
</script>

<template>
  <ul class="to-do-list">
    <ToDoItem 
      v-for="toDo in toDoList"
      :key="toDo.id" 
      :toDo="toDo"
      @update-to-do="emit('editToDo', $event)"
      @remove-to-do="emit('deleteToDo', $event)"
    />
  </ul>
</template>

<style lang="scss">
.to-do-list {
  padding-left: 30px;
  position: relative;
  overflow: hidden;

  &__items {
    padding-top: 5px;
    width: 100%;
    height: 450px;
    overflow-y: scroll;
    position: relative;
  }
}

.to-do-list__items::-webkit-scrollbar {
  width: 4px;
}

.to-do-list__items::-webkit-scrollbar-thumb {
  width: 4px;
  background: $main-orange;
  border-radius: 10px;
}

.to-do-list__items::-webkit-scrollbar-thumb:hover {
  background: $hover-orange; 
}
</style>
