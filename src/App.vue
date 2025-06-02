<script setup>
import Button from "./components/Button.vue";
import ScoreDisplay from "./components/ScoreDisplay.vue";
import HeardIcon from "./icons/HeardIcon.vue";
import Card from "./components/Card.vue";
import {ref} from "vue";

const btnStyle = 'button';

let score = ref(0);
let card = ref({
  word: 'pollination',
  translation: 'опыление',
  state: 'closed',
  status: 'pending',
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
    <Button buttonText = 'Начать игру'  >
    </Button>

    <Card v-bind="card">
    </Card>
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
  display: flex;
  align-items: center;
  justify-content: space-between;
}

.nav__text {
  color: #222222;
  font-weight: 700;
  text-transform: uppercase;
}
</style>
