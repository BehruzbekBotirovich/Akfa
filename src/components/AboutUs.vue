<template>
    <div>
        <h1 class="text-center font-bold text-2xl py-8">Наши услуги</h1>
        <div class="main-container flex justify-between flex-wrap">
            <div class="card" @click="showModal(1)" data-aos="fade-right" data-aos-duration="500" data-aos-delay="200">
                <div class="  w-11/12 lg:w-7/12 relative" style="z-index: 3;">
                    <div class="flex items-center gap-4 mb-4">
                        <img src="../assets/images/oyna.png" alt="">
                        <h1 class="text-2xl font-semibold">Установка пластиковых окон</h1>
                    </div>
                    <p>Устанавливаем пластиковые окна Rehau от проверенного производителя с гарантией качества</p>
                </div>
                <div class="filter"></div>
                <div class="bg-img"><img src='../assets/images/RecBg1.png' alt=""></div>
                <button class="more-info"> Подробнее</button>
            </div>

            <div class="card" @click="showModal(2)" data-aos="fade-left" data-aos-duration="500" data-aos-delay="200">
                <div class="w-11/12 lg:w-7/12 relative" style="z-index: 3;">
                    <div class="flex items-center gap-4 mb-4">
                        <img src="../assets/images/balkon.png" alt="">
                        <h1 class="text-2xl font-semibold">Остекление балконов и лоджий</h1>
                    </div>
                    <p>Занимаемся остеклением и отделкой балконов и лоджий. Теплое и холодное остекление, изготовление
                        выносов и крыш. Беремся за сложные объекты</p>
                </div>
                <div class="filter"></div>
                <div class="bg-img bottom-0"><img src='../assets/images/RecBg2.png' alt=""></div>
                <button class="more-info"> Подробнее</button>
            </div>

            <div class="card" @click="showModal(3)" data-aos="fade-right" data-aos-duration="500" data-aos-delay="400">
                <div class="w-11/12 lg:w-7/12 relative" style="z-index: 3;">
                    <div class="flex items-center gap-4 mb-4">
                        <img src="../assets/images/kotej.png" alt="">
                        <h1 class="text-2xl font-semibold">Остекление
                            коттеджей и дач</h1>
                    </div>
                    <p>Устанавливаем пластиковые окна Rehau от проверенного производителя с гарантией качества</p>
                </div>
                <div class="filter"></div>
                <div class="bg-img"><img src='../assets/images/RecBg3.png' alt=""></div>
                <button class="more-info"> Подробнее</button>
            </div>

            <div class="card" @click="showModal(4)" data-aos="fade-left" data-aos-duration="500" data-aos-delay="400">
                <div class="w-11/12 lg:w-7/12 relative" style="z-index: 3;">
                    <div class="flex items-center gap-4 mb-4">
                        <img src="../assets/images/obyekt.png" alt="">
                        <h1 class="text-2xl font-semibold">Остекление
                            корпоративных объектов
                        </h1>
                    </div>
                    <p>Устанавливаем пластиковые окна Rehau от проверенного производителя с гарантией качества</p>
                </div>
                <div class="filter"></div>
                <div class="bg-img"><img src='../assets/images/RecBg4.png' alt=""></div>
                <button class="more-info"> Подробнее</button>
            </div>
        </div>

        <a-modal v-model:visible="modals[1]" width="1000px" style="top: 20px" :footer="false" title="Наши услуги"
            @ok="handleOk(1)">
            <ServiseWindow></ServiseWindow>
        </a-modal>
        <a-modal v-model:visible="modals[2]" width="1000px" style="top: 20px" :footer="false" title="Наши услуги"
            @ok="handleOk(2)">
            <BalkonWindow />
        </a-modal>
        <a-modal v-model:visible="modals[3]" width="1000px" style="top: 20px" :footer="false" title="Наши услуги"
            @ok="handleOk(3)">
            <SetupWindow />
        </a-modal>
        <a-modal v-model:visible="modals[4]" width="1000px" style="top: 20px" :footer="false" title="Наши услуги"
            @ok="handleOk(4)">
            <ObjsetWindow />
        </a-modal>
    </div>
</template>


<script setup>
import { ref } from 'vue';
import ServiseWindow from './windows/ServiseWindow.vue';
import BalkonWindow from './windows/BalkonWindow.vue'
import ObjsetWindow from './windows/ObjsetWindow.vue'
import SetupWindow from './windows/SetupWindow.vue'
const modals = ref({
    1: false,
    2: false,
    3: false,
    4: false
});

function showModal(modalNumber) {
    modals.value[modalNumber] = true;
}

function handleOk(modalNumber) {
    console.log(`Modal ${modalNumber} OK clicked`);
    modals.value[modalNumber] = false;
}
</script>


<style scoped>
.more-info {
    position: absolute;
    right: 40px;
    bottom: 14px;
    z-index: 15;
    text-decoration: underline;
    font-size: 18px;
    color: rgba(255, 255, 255, 0.7);
    text-shadow: 1px 1px 2px rgb(141, 141, 141), 0 0 1em rgb(117, 117, 151), 0 0 0.2em rgb(105, 105, 168);
}

.more-info:hover {
    color: rgba(255, 255, 255, 1);
}

.card {
    display: flex;
    align-items: center;
    min-height: 260px;
    z-index: 1;
    border-radius: 3px;
    width: 49.5%;
    padding: 30px 50px;
    position: relative;
    margin-bottom: 10px;
    box-shadow: rgba(0, 0, 0, 0.16) 0px 1px 4px;
    transition: all 1.3s ease;

    @media(max-width:760px) {
        width: 100%;
        padding: 15px 20px;
        min-height: 160px;
    }
}

.card:hover {
    box-shadow: rgba(0, 0, 0, 0.16) 0px 3px 6px, rgba(0, 0, 0, 0.23) 0px 3px 6px;
}

.bg-img {
    position: absolute;
    left: 0px;
    top: 0;
    width: 100%;
    height: 100%;
}

.bg-img>img {
    width: 100%;
    height: 100%;
    object-fit: cover;
}

.filter {
    position: absolute;
    width: 100%;
    height: 100%;
    top: 0;
    z-index: 1;
    left: 0;
    background: rgb(255, 255, 255);
    background: -moz-linear-gradient(90deg, rgba(255, 255, 255, 1) 41%, rgba(255, 255, 255, 0) 100%);
    background: -webkit-linear-gradient(90deg, rgba(255, 255, 255, 1) 41%, rgba(255, 255, 255, 0) 100%);
    background: linear-gradient(90deg, rgba(255, 255, 255, 1) 41%, rgba(255, 255, 255, 0) 100%);
    filter: progid:DXImageTransform.Microsoft.gradient(startColorstr="#ffffff", endColorstr="#ffffff", GradientType=1);
}
</style>