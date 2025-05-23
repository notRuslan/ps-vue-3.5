<script setup>
const {scoreValue = 0} = defineProps({
  scoreValue: Number,
});
</script>

<template>
<div class="score">
  <div class="score__value">{{ scoreValue }}</div>
  <slot />
</div>
</template>

<style scoped>

.score{
  display: flex;
  text-align: center;
  justify-content: center;
  align-items: center;
  border-radius: 36px;
  padding: 12px 24px;
  max-width: 110px;
  box-shadow: 0 0 4px 0 rgba(0, 0, 0, 0.15);
  background: #cce8ff;
  gap: 10px;
}

.score__value{
  color: var(--color-score);
  font-size: 16px;
  line-height: 150%;
  font-weight: 700;
}
</style>
