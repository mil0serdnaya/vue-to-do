<script setup>
import ToDoItem from './ToDoItem.vue';

const props = defineProps({
  toDoList: {
    type: Array,
    required: true
  }
});

const emit = defineEmits(['editToDo', 'deleteToDo']);

const handleEdit = (updatedToDo) => emit('editToDo', updatedToDo);
const handleDelete = (toDoId) => emit('deleteToDo', toDoId);
</script>

<template>
  <ul class="to-do-list">
    <ToDoItem 
      v-for="toDo in toDoList"
      :key="toDo.id"
      :toDo="toDo"
      @updateToDo="handleEdit"
      @removeToDo="handleDelete"
    />
  </ul>
</template>

<style lang="scss" scoped>
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

  &__items::-webkit-scrollbar {
    width: 4px;
  }

  &__items::-webkit-scrollbar-thumb {
    background: $main-orange;
    border-radius: 10px;
  }

  &__items::-webkit-scrollbar-thumb:hover {
    background: $hover-orange;
  }
}
</style>
