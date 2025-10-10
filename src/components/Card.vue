<script setup>

const props = defineProps({
    num: Number,
    word: String
})

const emit = defineEmits({
    cardClick(value) {
        return value;
    }
})

const card = (event) => {

    emit("cardClick", event)
}

</script>

<template>
    <div class="card">
        <div class="card__wrap" @click="card('flip')">
            <div class="card__num">{{ props.num }}</div>
            <div class="card__word">{{ props.word }}</div>
            <div class="card__botom">Перевернуть</div>
        </div>
        <div class="card__btns">
            <button @click="card('no')">
                <img src="../assets/no.svg" alt="">
            </button>
            <button @click="card('yes')">
                <img src="../assets/yes.svg" alt="">
            </button>
        </div>
    </div>
</template>

<style scoped>
.card {
    background-color: var(--white);
    min-width: 250px;
    min-height: 380px;
    padding: 30px 20px;
    border-radius: 16px;
    cursor: pointer;
}
.card__wrap {
    display: flex;
    flex-direction: column;
    justify-content: space-between;
    border: 1px solid var(--light-blue);
    border-radius: 12px;
    height: 100%;
}
.card__num {
    background-color: var(--white);
    width: fit-content;
    font-size: 14px;
    line-height: 1;
    padding: 0 5px;
    position: relative;
    transform: translate(8px, -50%);
}
.card__word {
    text-align: center;
    font-size: 18px;
    line-height: 1;
}
.card__botom {
    background-color: var(--white);
    width: fit-content;
    align-self: center;
    font-weight: 700;
    font-size: 12px;
    letter-spacing: 12%;
    line-height: 1;
    text-transform: uppercase;
    padding: 0 5px;
    position: relative;
    transform: translate(0,50%);
}
.card__btns {
    display: flex;
    align-items: center;
    justify-content: center;
    gap: 16px;
}
</style>