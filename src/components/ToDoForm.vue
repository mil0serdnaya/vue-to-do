<script setup>

</script>

<template>
  <div class="to-do-form">
    <input type="text" class="to-do-input" placeholder="What needs to be done?">
    <input type="text" class="to-do-input" placeholder="Additional description for your todo">
  </div>
</template>

<style lang="scss">
@import "@/assets/styles/_vars.scss";

.to-do-form {
  padding: 20px;
}

.to-do-input {
  display: block;
  width: 100%;
  outline: none;
}
</style>