<script setup>

import ButtonsStatuses from "./ButtonsStatuses.vue";
import SmallOKIcon from "../icons/SmallOKIcon.vue";
import SmallNotOKIcon from "../icons/SmallNotOKIcon.vue";

const emit = defineEmits(['cardRotate']);
const props = defineProps({
  word: String,
  translation: String,
  state: String,
  status: String,
  cardNumber: Number,
});

function rotate() {
  emit('cardRotate');
}

</script>

<template>
  <div class="card">
    <div class="card-number">{{ cardNumber }}</div>
    <div v-if="status === 'success'" class="card-status" :class="status">
      <SmallOKIcon class="status-icon-lg"/>
    </div>
    <div v-if="status === 'fail'" class="card-status" :class="status">
      <SmallNotOKIcon class="status-icon-lg"/>
    </div>
    <div class="card-content">
      <div class="main-text">
        <div v-if="state === 'closed'">{{ word }}</div>
        <div v-else>{{ translation }} : {{ status }}</div>
      </div>
    </div>
    <div v-if="state === 'opened' && status === 'pending'" class="bottom-text">
      <ButtonsStatuses/>
    </div>
    <div v-else-if="status === 'pending'" class="bottom-text" @click="rotate()">перевернуть</div>
    <div v-if="status !== 'pending'" class="bottom-text" @click="rotate()">завершено</div>
  </div>
</template>

<style scoped>
.card {
  width: 250px;
  height: 376px;
  background: var(--color-secondary);
  color: var(--color-primary);
  border-radius: 16px;
  box-shadow: 0 0 16px 0 rgba(0, 0, 0, 0.1);
  position: relative;
  overflow: hidden;
  display: flex;
  flex-direction: column;
  padding: 20px;
}

.card-number {
  position: absolute;
  top: 12px;
  left: 35px;
  font-size: 14px;
  font-weight: 400;
  z-index: 2;
}

.card-status {
  position: absolute;
  top: 2px;
  left: 100px;
  z-index: 2;
}

.card::before {
  content: "";
  position: absolute;
  top: 20px;
  left: 20px;
  right: 20px;
  bottom: 20px;
  border: 1px solid #cce8ff;
  border-radius: 12px;
  pointer-events: none;
}

.card-content {
  flex: 1;
  display: flex;
  justify-content: center;
  align-items: center;
  padding: 80px 30px 30px;
}

.main-text {
  font-size: 18px;
  font-weight: 400;
  text-align: center;
}

.bottom-text {
  position: absolute;
  bottom: 12px;
  left: 50%;
  transform: translateX(-50%);
  font-size: 12px;
  font-weight: 700;
  color: #222222;
  letter-spacing: 0.12em;
  text-transform: uppercase;
  line-height: 150%;
  z-index: 2;
}
</style>
