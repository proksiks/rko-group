<template>
  <label class="checkbox">
    <input type="checkbox" class="checkbox__input" />
    <div class="checkbox__check"></div>
    <div class="checkbox__text"><slot /></div>
  </label>
</template>

<script setup></script>

<style scoped lang="scss">
  @import "@/assets/scss/components/_checkbox.scss";
</style>
