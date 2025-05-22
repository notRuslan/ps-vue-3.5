<script setup>

</script>

<template>
<button class="button">
  <slot />
</button>
</template>

<style scoped>
.button{
  border: none;
  color: var(--color-secondary);
  background-color: var(--color-third);
  font-size: 24px;
  line-height: 150%;
  border-radius: 100px;
  padding: 16px 10px;
  width: 335px;
  display: block;
  text-align: center;
}

.button:hover {
  background: var(--color-third--invert);
}
</style>
