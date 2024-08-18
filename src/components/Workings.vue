<template>
    <div class="main-container mb-16">
        <h1 class="text-center text-3xl text-gray-900 font-semibold py-12">О компании</h1>
        <ul class="navbar">
            <li :class="{ active: about }" @click="showSection('about')">Описание</li>
            <li :class="{ active: how }" @click="showSection('how')">Как мы работаем</li>
            <li :class="{ active: sertifi }" @click="showSection('sertifi')">Сертификаты</li>
        </ul>

        <transition name="fade">
            <AboutCompany v-if="about" />
        </transition>

        <transition name="fade">
            <HowWorking v-if="how" />
        </transition>

        

        <transition name="fade">
            <SertificateSlider v-if="sertifi" />
        </transition>
    </div>
</template>

<script setup>
import { ref } from 'vue'
import AboutCompany from './windows/AboutCompany.vue'
import HowWorking from './windows/HowWorking.vue'
import SertificateSlider from './windows/SertificateSlider.vue'

const about = ref(true)
const how = ref(false)
const otziv = ref(false)
const sertifi = ref(false)

const showSection = (section) => {
    about.value = section === 'about'
    how.value = section === 'how'
    otziv.value = section === 'otziv'
    sertifi.value = section === 'sertifi'
}
</script>

<style scoped>
.navbar {
    display: flex;
    gap: 20px;
    justify-content: center;
    margin-bottom: 30px;
}

.navbar>li {
    padding: 8px 25px;
    border-radius: 6px;
    font-size: 18px;
    font-weight: 400;
    line-height: 21.09px;
    cursor: pointer;
}

.navbar>li:hover {
    background: #efefef;
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
