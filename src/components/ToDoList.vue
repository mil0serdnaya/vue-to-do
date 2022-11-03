<script>
export default {
  data() {
    return {
      toDoItems: [
        {
          id: 1,
          title: 'delectus aut autem',
          subtitle: 'laboriosam mollitia et enim quasi adipisci quia provident illum'
        },
        {
          id: 2,
          title: 'quo laboriosam deleniti aut qui',
        },
        {
          id: 3,
          title: 'laboriosam mollitia et enim quasi adipisci quia provident illum',
        },
        {
          id: 4,
          title: 'repellendus sunt dolores architecto voluptatum',
          subtitle: 'accusamus eos facilis sint et aut voluptatem'
        },
        {
          id: 5,
          title: 'repellendus sunt dolores architecto voluptatum',
          subtitle: 'accusamus eos facilis sint et aut voluptatem'
        },
        {
          id: 6,
          title: 'repellendus sunt dolores architecto voluptatum',
          subtitle: 'accusamus eos facilis sint et aut voluptatem'
        },
        {
          id: 7,
          title: 'repellendus sunt dolores architecto voluptatum',
          subtitle: 'accusamus eos facilis sint et aut voluptatem'
        },
        {
          id: 8,
          title: 'repellendus sunt dolores architecto voluptatum',
          subtitle: 'accusamus eos facilis sint et aut voluptatem'
        },
        {
          id: 9,
          title: 'repellendus sunt dolores architecto voluptatum',
          subtitle: 'accusamus eos facilis sint et aut voluptatem'
        },
      ]
    }
  }
}
</script>

<template>
  <article class="to-do-list">
    <div class="to-do-list__container">
      <ul class="to-do-list-items">
        <li v-for="(toDo, index) in toDoItems" :key="index" class="to-do-list-item">
          <input type="checkbox" :id="toDo.id" />
          <label :for="toDo.id">
            <span class="to-do-list-item__title">{{ toDo.title }}</span>
            <span v-if="toDo.subtitle" class="to-do-list-item__subtitle">{{ toDo.subtitle }}</span>
          </label>
        </li>
      </ul>
    </div>
  </article>
</template>

<style lang="scss">
@import "../assets/scss/components/_to-do-list.scss";
</style>
