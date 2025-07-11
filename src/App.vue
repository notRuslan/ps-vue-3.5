<script setup>
import Button from "./components/Button.vue";
import ScoreDisplay from "./components/ScoreDisplay.vue";
import HeardIcon from "./icons/HeardIcon.vue";
import Card from "./components/Card.vue";
import {onMounted, ref} from "vue";

const API_ENDPOINT = 'http://localhost:8080/api';


let score = ref(0);
/*let card = ref({
  word: 'pollination',
  translation: 'опыление',
  state: 'closed',
  status: 'pending',
});*/

let data = ref([]);


async function getCards() {
  score.value = 0;
  // eslint-disable-next-line no-undef
  const res = await fetch(`${API_ENDPOINT}/random-words`);
  if (res.status != 200) {
    console.error('Error fetching data');
  }
  data.value = await res.json();

  const tempData = data.value?.map((item) => ({
    ...item,
    state: 'closed',
    status: 'pending',
  }));

  data.value = tempData;
}

onMounted(() => {
  getCards();
});

let isStartedGame = false;

function flipCard(index) {
  data.value[index].state = 'opened';
}

function successAnswer(index) {
  data.value[index].status = 'success';
  score.value += 10;
}

function wrongAnswer(index) {
  data.value[index].status = 'fail';
  score.value -= 4;
}

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
    <Button button-text='Начать игру' @start-game="getCards"/>
    <div class="card-list">
      <Card
          v-for="(card, index) in data"
          v-bind="card"
          :key="`${card.word} + ${index}`"
          :card-number="index + 1"
          @card-rotate="flipCard(index)"
          @right-answer="successAnswer(index)"
          @wrong-answer="wrongAnswer(index)"
      >
      </Card>
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
