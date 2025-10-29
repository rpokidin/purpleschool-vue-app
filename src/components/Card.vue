<script setup>
import { ref } from 'vue';

const isClose = ref(true)

const { word } = defineProps({
    //num: String,
    word: String
})

const emit = defineEmits({
    cardClick(value) {
        return value;
    }
})

const card = (event) => {
    isClose.value = false
    emit("cardClick", event)
}

</script>

<template>
    <div class="card">
        <div class="card__border">
            <div class="card__top">
                <!--div class="card__top-num">{{ num }}</div-->
                <img class="card__top-ico" src="../assets/success-big.svg" alt="">
            </div>
            <div class="card__word" @click="card('flip')">{{ word }}</div>
            <div class="card__botom">
                <div class="card__botom-status" v-if="isClose">Перевернуть</div>
                <template v-else>
                    <button @click="card('no')">
                        <img src="../assets/no.svg" alt="">
                    </button>
                    <button @click="card('yes')">
                        <img src="../assets/yes.svg" alt="">
                    </button>
                </template>
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
    padding: 0 5px;
}
.card__top-ico {
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
    font-size: 18px;
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