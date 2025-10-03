<script setup></script>

<template>
    <button class="btn">
        <slot></slot>
    </button>
</template>

<style scoped>
.btn {
    background: var(--btn-default);
    display: inline-flex;
    justify-content: center;
    min-width: 335px;
    font-size: 24px;
    color: var(--white);
    padding: 16px;
    border-radius: 100px;
}
.btn:hover {
    background: var(--btn-hover);
}
</style>