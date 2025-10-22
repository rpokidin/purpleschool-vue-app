<script setup>

import Logo from './components/Logo.vue';
import Score from './components/Score.vue';
import Button from './components/Button.vue';
import Card from './components/Card.vue';
import { ref } from 'vue';

const score = ref(0)

const data = [
  {
    num: "01",
    word: "unadmitted",
    translation: "непризнанный",
    state: "closed",
    status: "pending" //success | fail | pending
  },
  {
    num: "02",
    word: "armour-piercer",
    translation: "бронебойный",
    state: "opened",
    status: "pending"
  },
]

function cardEvent(value) {
  console.log(value);
}

</script>

<template>
  <header class="header">
    <Logo />
    <Score :score="score" />
  </header>
  <main class="main">
    <div class="card-list">
      <Card v-for="item in data" v-bind="item" :key="item.num" @card-click="cardEvent" />
    </div>
    <Button>Начать игру</Button>
  </main> 
</template>

<style scoped>
.header {
  display: flex;
  align-items: center;
  justify-content: space-between;
  margin-bottom: 50px;
}
.main {
  display: flex;
  flex-direction: column;
  width: 100%;
}
.main > .btn {
  align-self: center;
  align-content: center;
}
.card-list {
  display: flex;
  gap: 100px;
  margin-bottom: 50px;
}
</style>