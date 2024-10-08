<script setup>
import { ref, watch } from 'vue'
import EditIcon from './icons/EditIcon.vue'
import SaveIcon from './icons/SaveIcon.vue'
import DeleteIcon from './icons/DeleteIcon.vue'

const props = defineProps({
  toDo: {
    type: Object,
    required: true
  }
})

const emit = defineEmits(['updateToDo', 'removeToDo'])

const isEditing = ref(false)
const isEditButtonVisible = ref(true)
const title = ref(props.toDo.title)
const description = ref(props.toDo.description)

watch(() => props.toDo, (newToDo) => {
  title.value = newToDo.title
  description.value = newToDo.description
}, { immediate: true })

const startEditing = () => {
  isEditing.value = true
  isEditButtonVisible.value = false
}

const saveChanges = () => {
  emit('updateToDo', {
    id: props.toDo.id,
    title: title.value,
    description: description.value
  })
  stopEditing()
}

const stopEditing = () => {
  isEditing.value = false
  isEditButtonVisible.value = true
}

const deleteToDo = () => {
  emit('removeToDo', props.toDo.id)
}
</script>

<template>
  <li class="to-do-list-item">
    <div class="to-do-list-item__actions">
      <button v-if="isEditButtonVisible" @click="startEditing" class="action-btn">
        <EditIcon />
      </button>
      <button v-if="isEditButtonVisible" @click="deleteToDo" class="action-btn">
        <DeleteIcon />
      </button>
      <button v-if="isEditing" @click="saveChanges" class="action-btn">
        <SaveIcon />
      </button>
    </div>

    <div>
      <span v-if="!isEditing" class="to-do-list-item__title">{{ title }}</span>
      <input 
        v-if="isEditing"
        v-model="title"
        class="to-do-list-item__input"
        type="text"
        name="title" />
    </div>

    <div>
      <span v-if="!isEditing" class="to-do-list-item__description">{{ description }}</span>
      <input 
        v-if="isEditing"
        v-model="description"
        class="to-do-list-item__input"
        type="text"
        name="description" />
    </div>
  </li>
</template>

<style lang="scss">
.to-do-list-item {
  display: flex;
  flex-direction: column;
  position: relative;

  &__actions {
    display: flex;
    position: absolute;
    right: 0;
    top: 0;
    z-index: 1;
  }

  .action-btn {
    opacity: 0;
    transition: opacity 0.3s;
  }

  &:hover .action-btn {
    opacity: 1;
  }

  &__title, &__description {
    margin-bottom: 5px;
    font-size: 16px;
  }

  &__input {
    width: 100%;
    border: none;
    outline: none;
    background: transparent;
    font-size: 16px;
  }
}
</style>