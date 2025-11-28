<script setup>

import Logo from './components/Logo.vue';
import Score from './components/Score.vue';
import Button from './components/Button.vue';
import Card from './components/Card.vue';
import { ref } from 'vue';

const score = ref(0)
const words = ref(null)

function getData() {
  const API_ENDPOINT = "http://localhost:8080/api/random-words"
  fetch(API_ENDPOINT)
    .then(response => {
      if (!response.ok) {
        throw new Error('Ошибка запроса');
      }
      return response.json();
    })
    .then(data => {
      words.value = data.map(item => ({ ...item, status: 'pending' }))
    })
    .catch(error => {
      console.log(error);
    });

}

function cardEvent(word, status) {
  
  words.value.find(item => {
    if (item.word === word) {
      item.status = status
    }
  })

  switch (status) {
    case "success":
      score.value += 10
      break;
    case "fail":
      score.value -= 4
      break;
  }

}

</script>

<template>
  <header class="header">
    <Logo />
    <Score :score="score" />
  </header>
  <main class="main">
    <template v-if="words !== null">
      <div class="card-list">
        <Card 
          v-for="(item, index) in words" v-bind="item" :key="index"
          :num="index + 1"
          :word="item.word"
          :status="item.status"
          @card-click="cardEvent" 
        />
      </div>
    </template>
    <Button @click="getData">
      <template v-if="words !== null">Начать заново</template>
      <template v-else>Начать игру</template>
    </Button>
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
}
.main > .btn {
  align-self: center;
}
.card-list {
  display: flex;
  flex-wrap: wrap;
  gap: 100px;
  margin-bottom: 50px;
}
</style>