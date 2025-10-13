<script setup>
import { ref } from 'vue';

const props = defineProps({
    value: Number
})

const scoreVal = ref(props.value);
    
</script>

<template>
    <div class="score">
        <div class="score-val">{{ scoreVal }}</div>
        <img src="../assets/heart.svg" alt="">
    </div>
</template>

<style scoped>
.score {
    background-color: var(--light-blue);
    display: flex;
    align-items: center;
    gap: 10px;
    padding: 12px 24px;
    border-radius: 36px;
    box-shadow: 0px 0px 4px 0px #00000026;

}
.score-val {
    font-weight: 700;
    font-size: 16px;
    color: var(--blue);
}
</style>