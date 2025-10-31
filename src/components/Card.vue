<script setup>
import { ref } from 'vue';

const isFlip = ref(false);
const localStatus = ref(status);

const { num, word, translation, status } = defineProps({
    num: Number,
    word: String,
    translation: String,
    status: {
        type: String,
        default: "pending"
    }
})

/*
const emit = defineEmits({
    cardClick(value) {
        return value;
    }
})
*/

const card = (event) => {

    //emit("cardClick", event)

    switch (event) {
        case "flip":
            isFlip.value = true
            break;
        case "yes":
            isFlip.value = false
            localStatus.value = "success"
            break;
        case "no":
            isFlip.value = false
            localStatus.value = "fail"
            break;
    }

}
</script>

<template>
    <div class="card" :status="status">
        <div class="card__border">
            <div class="card__top">
                <div class="card__top-num">{{ num }}</div>
                <template v-if="localStatus == 'success'">
                    <img src="../assets/success-big.svg" alt="">
                </template>
                <template v-if="localStatus == 'fail'">
                    <img src="../assets/fail-big.svg" alt="">
                </template>
            </div>
            <div class="card__word" @click="card('flip')">
                <template v-if="isFlip">{{ translation }}</template>
                <template v-else>{{ word }}</template>
            </div>
            <div class="card__botom">
                <template v-if="isFlip">
                    <button @click="card('no')">
                        <img src="../assets/no.svg" alt="">
                    </button>
                    <button @click="card('yes')">
                        <img src="../assets/yes.svg" alt="">
                    </button>
                </template>
                <div v-else class="card__botom-status">
                    <template v-if="localStatus == 'pending'">
                    Перевернуть
                    </template>
                    <template v-else>
                    Завершено
                    </template>
                </div>
            </div>
        </div>
    </div>
</template>

<style scoped>
.card {
    background-color: var(--white);
    width: 250px;
    height: 380px;
    padding: 30px 20px;
    border-radius: 16px;
}
.card__border {
    display: flex;
    flex-direction: column;
    height: 100%;
    border: 1px solid var(--light-blue);
}
.card__border {
    border-radius: 12px;
    height: 100%;
}
.card__top {
    position: relative;
    top: -7px;
}
.card__top-num {
    background-color: var(--white);
    width: fit-content;
    font-size: 14px;
    line-height: 1;
    padding: 0 1px;
    margin-left: 16px;
}
.card__top > img {
    transform: translate(-50%,-50%);
    position: absolute;
    top: 50%;
    left: 50%;
    transform: translate(-50%,-50%);
}
.card__word {
    display: flex;
    align-items: center;
    justify-content: center;
    text-align: center;
    font-size: 18px;
    padding: 0 20px;
    cursor: pointer;
    flex-grow: 1;
}
.card__botom {
    background-color: var(--white);
    display: flex;
    align-items: center;
    align-self: center;
    gap: 16px;
    width: fit-content;
    height: 24px;
    padding: 0 5px;
    position: relative;
    bottom: -12px;
}
.card__botom button {
    font-weight: 700;
    font-size: 12px;
    letter-spacing: 12%;
    text-transform: uppercase;
}
</style>