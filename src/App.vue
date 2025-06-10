<script setup>
import Button from "./components/Button.vue";
import ScoreDisplay from "./components/ScoreDisplay.vue";
import HeardIcon from "./icons/HeardIcon.vue";
import Card from "./components/Card.vue";
import {computed, onMounted, ref} from "vue";

const API_ENDPOINT = 'http://localhost:8080/api';
const btnStyle = 'button';


let score = ref(0);
/*let card = ref({
  word: 'pollination',
  translation: 'опыление',
  state: 'closed',
  status: 'pending',
});*/

let data = ref([]);


async function getCards() {
  // eslint-disable-next-line no-undef
  const res = await fetch(`${API_ENDPOINT}/random-words`);
  if (res.status != 200) {
    console.error('Error fetching data');
  }
  data.value = await res.json();
}

let dataModified = computed(() => {
  if (!data.value) {
    return [];
  }
  return data.value?.map((item) => ({
    ...item,
    state: 'closed',
    status: 'pending',
  })) || []; // возвращаем пустой массив при отсутствии данных
});

onMounted(() => {
  getCards();
});

let isStartedGame = false;

// card.value.word = 'HHH';
</script>

<template>
  <header class="header container">
    <nav class="nav">
      <div class="nav__text">Запомни слово</div>
      <ScoreDisplay :score-value="score">
        <HeardIcon/>
      </ScoreDisplay>
    </nav>
  </header>
  <main class="main container">
    <Button buttonText='Начать игру' @click="getCards"/>
    <div class="card-list">
      <Card
          v-for="(card, index) in dataModified"
          v-bind="card"
          :key="`${card.word} + ${index}`"
          :card-number="index + 1"
      />
    </div>
  </main>
</template>

<style scoped>
.container {
  width: 100vw;
  max-width: 1440px;
  padding-left: 64px;
  padding-right: 62px;
}

nav {
  color: #000;
  display: flex;
  align-items: center;
  justify-content: space-between;
}

.nav__text {
  color: #222222;
  font-weight: 700;
  text-transform: uppercase;
}

.card-list {
  margin-top: 20px;
  display: flex;
  flex-wrap: wrap;
  gap: 20px;
}
</style>
