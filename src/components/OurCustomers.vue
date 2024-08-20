<template>
    <div class="bg-gray-100">


        <div class="main-container py-10">
            <h3 class="text-gray-500 py-4">Мы любим и ценим всех наших клиентов </h3>
            <div class="flex items-center justify-between mb-10">
                <h1 class="font-semibold text-4xl ">Наши клиенты </h1>
                <div class="flex gap-2">
                    <button @click="prevSlide" class="nav-button">
                        <LeftOutlined />
                    </button>
                    <button @click="nextSlide" class="nav-button">
                        <RightOutlined />
                    </button>
                </div>
            </div>
            <a-carousel ref="carousel" :dots="false" :slidesToShow="5" :infinite="true" :autoplay="true"
                :autoplaySpeed="4000">
                <div v-for="img in images" class="carousel-card ">
                    <img :src="img" alt="">
                </div>
            </a-carousel>
        </div>


    </div>

</template>
<script setup>
import { ref } from 'vue';
import { LeftOutlined, RightOutlined } from '@ant-design/icons-vue';
const images = ref([slide1, slide2, slide3, slide4, slide5, slide6, slide7, slide8, slide9, slide10])

import slide1 from '@/assets/images/client1.png';
import slide2 from '@/assets/images/client2.png';
import slide3 from '@/assets/images/client2.png';
import slide4 from '@/assets/images/client3.png';
import slide5 from '@/assets/images/client4.png';
import slide6 from '@/assets/images/client1.png';
import slide7 from '@/assets/images/client2.png';
import slide8 from '@/assets/images/client4.png';
import slide9 from '@/assets/images/client3.png';
import slide10 from '@/assets/images/client2.png';


const carousel = ref(null);

const prevSlide = () => {
    carousel.value.prev();
};
const nextSlide = () => {
    carousel.value.next();
};
</script>

<style scoped>
.carousel-card {
    padding: 10px;
}

:deep(.carousel-card img) {
    object-fit: cover;
    width: 100%;
    height: 100%;
    border-radius: 10px;

}

.nav-button {
    font-size: 20px;
    color: white;
    padding: 10px;
    background: #1d4ed8;
    border-radius: 6px;
    display: flex;
    transition: all 0.3;
}

.nav-button:hover {
    opacity: 0.8;
}
</style>