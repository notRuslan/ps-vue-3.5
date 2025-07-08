<script setup>

import IconOk from "../icons/IconOk.vue";
import IconNotOk from "../icons/IconNotOk.vue";
import StatusButton from "./Statuses/StatusButton.vue";

const emit = defineEmits(['right-answer', 'wrong-answer']);

function rightAnswer() {
  emit('right-answer');
}

function wrongAnswer() {
  emit('wrong-answer');
}

</script>

<template>
  <div class="buttons-statuses">
    <StatusButton @click="wrongAnswer()">
      <IconNotOk/>
    </StatusButton>
    <StatusButton @click="rightAnswer()">
      <IconOk/>
    </StatusButton>
  </div>

</template>

<style scoped>
.buttons-statuses {
  display: flex;
  justify-content: space-between;
  align-items: center;
  gap: 40px;
}
</style>
