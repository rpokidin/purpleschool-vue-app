<script setup>

import Logo from './components/Logo.vue';
import Score from './components/Score.vue';
import Button from './components/Button.vue';
import Card from './components/Card.vue';
import { onMounted, ref } from 'vue';

const score = ref(0)
const words = ref(null)

onMounted(() => {
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
})


function cardEvent(value) {
  
  console.log(value);

    switch (value) {
        case "no":
            status = "no"
            break;
    }
}

console.log(words)

</script>

<template>
  <header class="header">
    <Logo />
    <Score :score="score" />
  </header>
  <main class="main">
    <div class="card-list">
      <Card 
        v-for="(item, index) in words" v-bind="item" :key="index"
        :num="index + 1"
        :word="item.word"
        :status="item.status"
        @card-click="cardEvent" 
      />
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
  flex-wrap: wrap;
  gap: 100px;
  margin-bottom: 50px;
}
</style>