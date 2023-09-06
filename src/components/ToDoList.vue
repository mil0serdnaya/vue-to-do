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
          title: 'delectus aut autem',
          subtitle: 'laboriosam mollitia et enim quasi adipisci quia provident illum'
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
        {
          id: 10,
          title: 'repellendus sunt dolores architecto voluptatum',
        },
        {
          id: 11,
          title: 'repellendus sunt dolores architecto voluptatum',
          subtitle: 'accusamus eos facilis sint et aut voluptatem'
        },
        {
          id: 12,
          title: 'repellendus sunt dolores architecto voluptatum',
          subtitle: 'accusamus eos facilis sint et aut voluptatem'
        },
        {
          id: 13,
          title: 'repellendus sunt dolores architecto voluptatum',
          subtitle: 'accusamus eos facilis sint et aut voluptatem'
        },
        {
          id: 14,
          title: 'repellendus sunt dolores architecto voluptatum',
        },
        {
          id: 15,
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
    <ul class="to-do-list__items">
      <li
        v-for="(toDo, index) in toDoItems"
        :key="index"
        class="to-do-list-item">
        <input type="checkbox" :id="toDo.id" />
        <label :for="toDo.id">
          <span class="to-do-list-item__title">{{ toDo.title }}</span>
          <span v-if="toDo.subtitle" class="to-do-list-item__subtitle">{{ toDo.subtitle }}</span>
        </label>
      </li>
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

.to-do-list-item {
  display: flex;
  align-items: center;

  &:last-child {
    background: linear-gradient(180deg, rgba(37, 46, 66, 0) 0%, #252E42 67.19%);
  }

  input[type="checkbox"] {
    position: absolute;
    opacity: 0;
    &:hover + label:before {
      transition: background .3s;
      background: rgba(255, 132, 105, 0.2);
    }
  }

  label {
    position: relative;
    padding-left: 35px;
    margin-bottom: 15px;
    cursor: pointer;

    &:hover span {
      transition: color .3s;
      color: $main-orange;
    }
  }

  input[type="checkbox"] + label:before {
    content: '';
    width: 20px;
    height: 20px;
    position: absolute;
    top: 50%;
    left: 0;
    transform: translateY(-50%);
    background: $description-text-color;
    border-radius: 6px;
    cursor: pointer;
  }

  input[type="checkbox"]:checked + label:before {
    background: $main-orange;
  }

  input[type="checkbox"]:checked + label:after {
    content: '';
    position: absolute;
    left: 5px;
    top: 50%;
    background: white;
    width: 2px;
    height: 2px;
    box-shadow: 
      2px 0 0 white,
      4px 0 0 white,
      4px -2px 0 white,
      4px -4px 0 white,
      4px -6px 0 white,
      4px -8px 0 white;
    transform: rotate(45deg);
  }

  input[type="checkbox"]:checked + label {
    span {
      text-decoration: line-through;
      color: $description-text-color;
    }
  }

  &__title {
    font-weight: 500;
    font-size: 16px;
    line-height: 20px;
    color: $title-text-color;
    display: block;
    margin-bottom: 3px;
    max-width: 324px;
  }

  &__subtitle {
    display: block;
    font-weight: 400;
    font-size: 12px;
    line-height: 14px;
    color: $description-text-color;
    position: relative;
    &::after {
      content: '';
      display: block;
      width: 30px;
      height: 30px;
      position: absolute;
      top: 0;
      right: 0;
      background: linear-gradient(180deg, #252E42 9.38%, rgba(37, 46, 66, 0) 66.15%);
      transform: rotate(90deg);
    }
  }
}

</style>
