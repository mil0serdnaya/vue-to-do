<script setup>
  import ToDoItem from './ToDoItem.vue'
</script>

<template>
  <article class="to-do-list">
    <ul class="to-do-list__items">
      <ToDoItem />
    </ul>
  </article>
</template>

<style lang="scss">
@import "@/assets/styles/_vars.scss";

.to-do-list {
  padding-left: 30px;
  position: relative;
  overflow: hidden;

  &:after {
    content: '';
    position: absolute;
    bottom: 0;
    width: 100%;
    height: 40px;
    background: linear-gradient(180deg, rgba(37, 46, 66, 0) 0%, #252E42 67.19%);
  }

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
