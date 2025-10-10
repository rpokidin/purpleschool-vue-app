<script setup>
import Logo from './components/Logo.vue';
import Score from './components/Score.vue';
import Button from './components/Button.vue';
import Card from './components/Card.vue';

function cardEvent(value) {
  console.log(value);
}
</script>

<template>
  <header class="header">
    <Logo />
    <Score value="0" />
  </header>
  <main class="main">
    <div class="card-list">
      <Card num="01" word="unadmitted" @card-click="cardEvent" />
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