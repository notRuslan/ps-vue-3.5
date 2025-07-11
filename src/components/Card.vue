<script setup>

import ButtonsStatuses from "./ButtonsStatuses.vue";
import IconOk from "../icons/IconOk.vue";
import IconNotOk from "../icons/IconNotOk.vue";

const emit = defineEmits(['card-rotate', 'right-answer', 'wrong-answer']);
const props = defineProps({
  word: String,
  translation: String,
  state: String,
  status: String,
  cardNumber: Number,
});

function rotate() {
  emit('card-rotate');
}

</script>

<template>
  <div class="card" :class="{flipped: state === 'opened'}">
    <div class="card-inner">
      <!-- Передняя сторона -->
      <div class="card-face card-front">
        <div class="card-number">{{ cardNumber }}</div>
        <div v-if="status === 'success'" class="card-status" :class="status">
          <IconOk :size="40"/>
        </div>
        <div v-if="status === 'fail'" class="card-status" :class="status">
          <IconNotOk :size="40"/>
        </div>
        <div class="card-content">
          <div class="main-text">{{ word }}</div>
        </div>
        <div v-if="status === 'pending'" class="bottom-text" @click="rotate()">
          перевернуть
        </div>
        <div v-if="status !== 'pending'" class="bottom-text">завершено</div>
      </div>

      <!-- Задняя сторона -->
      <div class="card-face card-back">
        <div class="card-number">{{ cardNumber }}</div>
        <div v-if="status === 'success'" class="card-status" :class="status">
          <IconOk :size="40"/>
        </div>
        <div v-if="status === 'fail'" class="card-status" :class="status">
          <IconNotOk :size="40"/>
        </div>
        <div class="card-content">
          <div class="main-text">{{ translation }}</div>
        </div>
        <div v-if="status === 'pending'" class="bottom-text">
          <ButtonsStatuses
              @right-answer="() => {emit('right-answer')}"
              @wrong-answer="() => {emit('wrong-answer')}"
          />
        </div>
        <div v-if="status !== 'pending'" class="bottom-text">завершено</div>
      </div>
    </div>
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
  perspective: 1000px;
}

.card-inner {
  position: relative;
  width: 100%;
  height: 100%;
  transform-style: preserve-3d;
  transition: transform 0.6s;
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
  top: 8px;
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
  cursor: pointer;
}


.card-face {
  position: absolute;
  width: 100%;
  height: 100%;
  backface-visibility: hidden;
  display: flex;
  flex-direction: column;
  padding: 20px;
}

.card-front {
  z-index: 2;
}

.card-back {
  transform: rotateY(180deg);
}

.card.flipped .card-inner {
  transform: rotateY(180deg);
}


</style>
