<template>
    <div class="relative main-container py-10 bg-white border-2">
        <h1 class="text-2xl font-semibold text-center mb-8">Portfolio</h1>
        <div class="carousel-container w-full  flex items-center justify-between">
            <!-- Кнопки навигации -->
            <button @click="prev" class="prev">
                <svg width="22" height="42" viewBox="0 0 22 42" fill="none" xmlns="http://www.w3.org/2000/svg">
                    <path d="M21 1L1 21L21 41" stroke="black" />
                    <path d="M21 1L1 21L21 41" stroke="#8F8F8F" />
                </svg>
            </button>

            <div class="carousel-wrapper w-11/12 overflow-hidden">
                <div class="carousel-track" :style="{ transform: `translateX(-${currentIndex * 25}%)` }">
                    <div v-for="(item) in images" :key="index" class="img-container">

                        <a-image :src="item" class="rasm" width="100%"> </a-image>
                    </div>
                </div>
            </div>

            <button @click="next" class="next">
                <svg width="22" height="42" viewBox="0 0 22 42" fill="none" xmlns="http://www.w3.org/2000/svg">
                    <path d="M0.5 1L20.5 21L0.5 41" stroke="black" />
                    <path d="M0.5 1L20.5 21L0.5 41" stroke="#8F8F8F" />
                </svg>
            </button>
        </div>
    </div>
</template>
<script setup>
import { ref } from 'vue';
import slide1 from '@/assets/slide_images/slide1.jpg';
import slide2 from '@/assets/slide_images/slide2.jpg';
import slide3 from '@/assets/slide_images/slide3.jpg';
import slide4 from '@/assets/slide_images/slide4.jpg';
import slide5 from '@/assets/slide_images/slide5.jpg';
import slide6 from '@/assets/slide_images/slide6.jpg';
import slide7 from '@/assets/slide_images/slide7.jpg';
import slide8 from '@/assets/slide_images/slide8.jpg';
import slide9 from '@/assets/slide_images/slide9.jpg';
import slide10 from '@/assets/slide_images/slide10.jpg';
import slide11 from '@/assets/slide_images/slide11.jpg';
import slide12 from '@/assets/slide_images/slide12.jpg';
import slide13 from '@/assets/slide_images/slide13.jpg';
import slide14 from '@/assets/slide_images/slide14.jpg';





const images = ref([
    slide1, slide2, slide3, slide4, slide5, slide6, slide7, slide8, slide9, slide10, slide11, slide12, slide13, slide14
]);

const currentIndex = ref(0);

const next = () => {
    if (currentIndex.value < images.value.length - 4) {
        currentIndex.value++;
    }
    else {
        currentIndex.value = 1
    }
};

const prev = () => {
    if (currentIndex.value > 0) {
        currentIndex.value--;
    } else {
        currentIndex.value = images.value.length - 4
    }
};
</script>
<style scoped>
.carousel-container {
    display: flex;
    align-items: center;
    justify-content: center;
}

.carousel-wrapper {
    overflow: hidden;
}

:deep(.rasm) {
    height: 100%;
    object-fit: cover;
}

.carousel-track {
    display: flex;
    transition: transform 0.3s ease-in-out;
}

:deep(.ant-image) {
    height: 15rem;
    width: 15rem;
}

.img-container {
    flex: 0 0 25%;
    box-sizing: border-box;
    padding: 0 10px;
}

img {
    display: block;
    width: 100%;
    height: auto;
}

.next:hover svg path {
    stroke: #f97316;
    transition: all 0.2s ease-in;
}

.prev:hover svg path {
    stroke: #f97316;
    transition: all 0.2s ease-in;
}

.prev {
    position: absolute;
    top: 50%;
    left: 10px;
    transform: translateY(-50%);
}

.next {
    position: absolute;
    top: 50%;
    right: 10px;
    transform: translateY(-50%);
}
</style>