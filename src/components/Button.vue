<script setup>

const props = defineProps({
  buttonText: String,
})
const emit = defineEmits(['startGame']);

function startGame(){
  emit('startGame');
}
</script>

<template>
<button class="button" @click="startGame()">
  {{ buttonText }}
</button>
</template>

<style scoped>
.button{
  color: var(--color-secondary);
  background-color: var(--color-third);
  font-size: 24px;
  line-height: 150%;
  border-radius: 100px;
  padding: 16px 10px;
  width: 335px;
  display: block;
  text-align: center;
  border: none;
}

.button:hover {
  background: var(--color-third--invert);
}
</style>
