<template>
    <div class="main-container mb-16 mt-12">
        <HowWorking />

    </div>
</template>

<script setup>
import { ref } from 'vue'
import HowWorking from './windows/HowWorking.vue'





</script>

<style scoped>
.navbar {
    margin: 0 auto;
    display: flex;
    gap: 20px;
    justify-content: center;
    margin-bottom: 30px;

    @media (max-width:610px) {
        gap: 10px;
    }
}

.navbar>li {
    padding: 8px 25px;
    border-radius: 6px;
    font-size: 18px;
    font-weight: 400;
    line-height: 21.09px;
    cursor: pointer;
    text-wrap: nowrap;

    @media (max-width:610px) {
        padding: 6px 10px;
        font-size: 14px;
    }
}

.navbar>li:hover {
    background: #EF7F04;
    color: white;
    opacity: 0.6;
    font-weight: 600;
}

.navbar>.active {
    background: #EF7F04;
    color: white;
    font-weight: 600;
}

.fade-enter-active,
.fade-leave-active {
    transition: opacity 0.5s ease;
}

.fade-enter-from,
.fade-leave-to {
    opacity: 0;
}
</style>
