<script setup>
import Button from "./components/Button.vue";
import ScoreDisplay from "./components/ScoreDisplay.vue";
import HeardIcon from "./icons/HeardIcon.vue";
import Card from "./components/Card.vue";

const btnStyle = 'button';

let score = 0;

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
    <Button :class=btnStyle>
      Начать игру
    </Button>

    <Card />
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
