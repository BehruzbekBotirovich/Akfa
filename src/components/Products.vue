<template>
    <div class="relative main-container mb-12   ">

        <a-carousel ref="carousel" dots="false" class="w4 self-center" :infinite="true">
            <div v-for="(item, index) in items" :key="index">
                <div class="my-slide ">
                    <div class=" w-1/2">
                        <a-image class="slide-rasm  md:w-full md:h-full object-contain aspect-square"
                            :src="item.img"></a-image>
                    </div>
                    <div class="  w-1/2  md:px-8 py-4 md:py-12 ">
                        <h1 class="text-orange-500  md:mb-6 text-3xl  font-semibold"></h1>
                        <p class="md:w-2/3 mb-2 md:mb-6 text-xl font-semibold">{{ item.name }}</p>
                        <!-- parametri -->
                        <div class="line">
                            <span> Количество камер: </span>
                            <div class="dots"></div>
                            <span> {{ item.camers }}</span>
                        </div>
                        <div class="line">
                            <span>Монтажная глубина рамы: </span>
                            <div class="dots"></div>
                            <span> {{ item.montaj }}</span>
                        </div>

                        <div class="line">
                            <span>Толщина стеклопакета: </span>
                            <div class="dots"></div>
                            <span> {{ item.widthSteklopaket }}</span>
                        </div>
                        <div class="line">
                            <span>Толщина армирующего профиля:</span>
                            <div class="dots"></div>
                            <span>{{ item.widthAramture }}</span>
                        </div>

                        <div class="line">
                            <span>Максимальный вес створки : </span>
                            <div class="dots"></div>
                            <span>{{ item.maxWeight }}</span>
                        </div>
                    </div>
                </div>
            </div>
        </a-carousel>

        <!-- Кнопки навигации -->
        <button @click="prev" class="prev ">


            <svg width="22" height="42" viewBox="0 0 22 42" fill="none" xmlns="http://www.w3.org/2000/svg">
                <path d="M21 1L1 21L21 41" stroke="black" />
                <path d="M21 1L1 21L21 41" stroke="#8F8F8F" />
            </svg>

        </button>
        <button @click="next" class="next ">
            <svg width="22" height="42" viewBox="0 0 22 42" fill="none" xmlns="http://www.w3.org/2000/svg">
                <path d="M0.5 1L20.5 21L0.5 41" stroke="black" />
                <path d="M0.5 1L20.5 21L0.5 41" stroke="#8F8F8F" />
            </svg>
        </button>


    </div>


</template>

<script setup>
import { ref } from 'vue';
// images
import quatro5800 from '@/assets/images/quatro5800.png'
import engelberg7000 from '@/assets/images/engelberg7000.png'
import quatro6000 from '@/assets/images/quattro6000.png'
import trio6000 from '@/assets/images/trio6000.png'

const carousel = ref(null);

const items = [
    {
        name: "Engelberg 7000",
        img: engelberg7000,
        montaj: '70 мм',
        camers: 5,
        widthSteklopaket: "6мм / 20мм",
        widthAramture: '2,0мм',
        maxWeight: '(Окна / Двери): 60 кг / 100 кг'
    },
    {
        name: "Trio 6000 ",
        img: trio6000,
        montaj: '60 мм',
        camers: 3,
        widthSteklopaket: "6мм / 20мм",
        widthAramture: '1,2мм',
        maxWeight: '(Окна / Двери): 80кг / 110кг'
    },
    {
        name: "Quatro 5800 ",
        img: quatro5800,
        montaj: '52 мм',
        camers: 4,
        widthSteklopaket: "6мм / 20мм",
        widthAramture: '1,2мм',
        maxWeight: '(Окна / Двери): 60 кг / 100 кг'
    },
    {
        name: "Quatro 6000",
        img: quatro6000,
        montaj: '60 мм',
        camers: 4,
        widthSteklopaket: "6мм / 20мм",
        widthAramture: '1,2мм',
        maxWeight: '(Окна / Двери): 70 кг / 110 кг'
    },

]

const next = () => {
    carousel.value.next();
};

const prev = () => {
    carousel.value.prev();
};
</script>

<style scoped>
.next:hover svg path {
    stroke: #f97316;
    transition: all 0.2s ease-in;
}

.prev:hover svg path {
    stroke: #f97316;
    transition: all 0.2s ease-in;
}

.slide-rasm {
    @media(max-width:760px) {
        width: 200px;
        height: 200px;
    }
}

.prev svg path {}

.w4 {
    margin-left: 30px;
    width: calc(100% - 60px);
}

.prev {
    position: absolute;
    top: calc(50% - 30px);
    left: 10px;
}

.next {
    position: absolute;
    top: calc(50% - 30px);
    right: 10px;
}

.my-slide {
    align-items: center;
    display: flex;
    border-radius: 5px;

    @media(max-width:760px) {
        /* display: block; */
    }
}


.line {
    display: flex;
    justify-content: space-between;
    width: 100%;
    white-space: nowrap;
    font-family: Arial, sans-serif;
    font-size: 16px;
    margin-bottom: 14px;

    @media(max-width:760px) {
        font-size: 14px;
    }
}

.dots {
    flex: 1;
    border-bottom: 1px dotted #000;
    margin: 0 10px;
    height: 0;
    position: relative;
    top: 14px;
}

:deep(.slick-dots li button) {
    background: #000;
}

:deep(.slick-dots li.slick-active button) {
    background: orange;
}

.top-1-2 {
    top: 50%;
}

.transform {
    transform: translateY(-50%);
}
</style>