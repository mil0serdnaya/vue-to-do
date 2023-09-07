<script setup>
  defineProps(['toDo'])
</script>

<template>
  <li class="to-do-list-item">
    <input type="checkbox" />
    <label>
      <span class="to-do-list-item__title">{{ toDo.title }}</span>
      <span class="to-do-list-item__subtitle">{{ toDo.description }}</span>
    </label>
  </li>
</template>

<style lang="scss">
@import "@/assets/styles/_vars.scss";

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
    background: $text-grey;
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
      color: $text-grey;
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
    color: $text-grey;
  }
}

</style>
