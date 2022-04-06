<template>
  <button class="button">
    <slot />
  </button>
</template>

<style scoped>
.button {
  background: blue;
  border-radius: 6px;
  padding: 5px 15px;
  color: white;
}
</style>
