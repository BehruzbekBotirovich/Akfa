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
                        <p class="md:w-2/3 mb-2 md:mb-6 font-semibold">{{ item.name }}</p>
                        <!-- parametri -->
                        <div class="line">
                            <span>Монтажная глубина: </span>
                            <div class="dots"></div>
                            <span> {{ item.montaj }}</span>
                        </div>
                        <div class="line">
                            <span>Толщина внешних стенок: </span>
                            <div class="dots"></div>
                            <span>{{ item.weight }}</span>
                        </div>

                        <div class="line">
                            <span>Толщина остекления: </span>
                            <div class="dots"></div>
                            <span>{{ item.width }}</span>
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
const carousel = ref(null);

const items = [
    {
        name: "THERMO 64 — ТЁПЛАЯ СЕРИЯ ",
        img: 'https://akfa.com.ua/wp-content/uploads/2018/02/main-bd38184ee5.png',
        montaj: '64 мм',
        weight: "1.2-1.5-2.0 мм",
        width: "20-32 мм"
    }
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