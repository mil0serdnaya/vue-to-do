<script setup>
  import { ref } from 'vue'

  defineProps(['toDo'])
  
  const emit = defineEmits(['updateToDo'])
  const isEditing = ref(false)
  const isEditBtnVisible = ref(true)
  const newTitleInput = ref(null)
  const newDescriptionInput = ref(null)

  const onClickEdit = () => {
    isEditing.value = !isEditing.value
    isEditBtnVisible.value = false
  }

  const onClickSave = (id, newTitle, newDescription) => {
    emit('updateToDo', { id, newTitle, newDescription })
    isEditing.value = false
    isEditBtnVisible.value = true
  }
</script>

<template>
  <li class="to-do-list-item">
    <div class="to-do-list-item__btns">
      <button class="btn--light-blue" v-show="isEditBtnVisible" @click="onClickEdit">Edit</button>
      <button class="btn--blue" v-show="isEditing" @click="onClickSave(toDo.id, newTitleInput.value, newDescriptionInput.value)">Save</button>
    </div>
    <div>
      <span class="to-do-list-item__title" v-show="!isEditing">{{ toDo.title }}</span>
      <input type="text"
             v-show="isEditing"
             class="to-do-list-item__input" 
             :value="toDo.title"
             ref="newTitleInput"
             name="title">
    </div>
    <div>
      <span class="to-do-list-item__description" v-show="!isEditing">{{ toDo.description }}</span>
      <input type="text"
              v-show="isEditing"
              class="to-do-list-item__input" 
              :value="toDo.description" 
              ref="newDescriptionInput"
              name="description">
    </div>
  </li>
</template>

<style lang="scss">
.to-do-list-item {
  display: flex;
  flex-direction: column;
  position: relative;
  cursor: pointer;

  .btn--light-blue {
    visibility: hidden;
    opacity: 0;
    transition: opacity .3s;
  }

  &:hover {
    .btn--light-blue {
      visibility: visible;
      opacity: 1;
    }
  }

  &__btns {
    display: flex;
    align-items: center;
    justify-content: flex-end;
    position: absolute;
    right: 0;
    z-index: 1;
  }
  
  &__title {
    font-weight: 500;
    font-size: 16px;
    line-height: 20px;
    color: $title-text-color;
    display: block;
    margin-bottom: 5px;
    max-width: 324px;
  }

  &__description {
    display: block;
    font-weight: 400;
    font-size: 14px;
    line-height: 16px;
    color: $text-grey;
  }

  // &:last-child {
  //   background: linear-gradient(180deg, rgba(37, 46, 66, 0) 0%, #252E42 67.19%);
  // }

  // input[type="checkbox"] {
  //   position: absolute;
  //   opacity: 0;
  //   &:hover + label:before {
  //     transition: background .3s;
  //     background: rgba(255, 132, 105, 0.2);
  //   }
  // }

  // label {
  //   position: relative;
  //   padding-left: 35px;
  //   margin-bottom: 15px;
  //   cursor: pointer;

  //   &:hover span {
  //     transition: color .3s;
  //     color: $main-orange;
  //   }
  // }

  // input[type="checkbox"] + label:before {
  //   content: '';
  //   width: 20px;
  //   height: 20px;
  //   position: absolute;
  //   top: 50%;
  //   left: 0;
  //   transform: translateY(-50%);
  //   background: $text-grey;
  //   border-radius: 6px;
  //   cursor: pointer;
  // }

  // input[type="checkbox"]:checked + label:before {
  //   background: $main-orange;
  // }

  // input[type="checkbox"]:checked + label:after {
  //   content: '';
  //   position: absolute;
  //   left: 5px;
  //   top: 50%;
  //   background: white;
  //   width: 2px;
  //   height: 2px;
  //   box-shadow: 
  //     2px 0 0 white,
  //     4px 0 0 white,
  //     4px -2px 0 white,
  //     4px -4px 0 white,
  //     4px -6px 0 white,
  //     4px -8px 0 white;
  //   transform: rotate(45deg);
  // }

  // input[type="checkbox"]:checked + label {
  //   span {
  //     text-decoration: line-through;
  //     color: $text-grey;
  //   }
  // }
}

</style>
