<script setup>
  import ToDoItem from './ToDoItem.vue'

  defineProps(['toDoList'])

  const emit = defineEmits(['editToDo'])
  const onUpdateToDo = (data) => {
    emit('editToDo', data)
  }
</script>

<template>
  <article class="to-do-list">
    <ul class="to-do-list__items">
      <ToDoItem v-for="toDo in toDoList.toDoItems" 
        :key="toDo.id"
        :toDo="toDo"
        @update-to-do="onUpdateToDo"
      />
    </ul>
  </article>
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
