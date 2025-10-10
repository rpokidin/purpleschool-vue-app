<script setup>
const props = defineProps({
    num: Number,
    word: String
})
const emit = defineEmits({
    turnOver(value) {
        return value;
    }
})

const card = () => {
    emit("turnOver", "Перевернуть")
}



</script>

<template>
    <div class="card" @click="card()">
        <div class="card__wrap">
            <div class="card__num">{{ props.num }}</div>
            <div class="card__word">{{ props.word }}</div>
            <div class="card__botom">
                Перевернуть
                <div class="card__botom-btns">
                    <button>
                        <img src="../assets/no.svg" alt="">
                    </button>
                    <button>
                        <img src="../assets/yes.svg" alt="">
                    </button>
                </div>
            </div>
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
    display: flex;
    flex-direction: column;
    align-items: center;
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
.card__botom-btns {
    width: 100%;
    display: flex;
    align-items: center;
    justify-content: space-between;
    gap: 16px;
}
</style>