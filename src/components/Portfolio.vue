<template>
    <div class="bg-gray-100 mt-6">
        <div class="main-container py-10">
            <div class="flex items-center justify-between mb-10">
                <h1 class="font-semibold text-4xl ">Наши проекты </h1>
                <div class="flex gap-2">
                    <button @click="prevSlide" class="nav-button">
                        <LeftOutlined />
                    </button>
                    <button @click="nextSlide" class="nav-button">
                        <RightOutlined />
                    </button>
                </div>
            </div>
            <a-carousel ref="carousel" :dots="false" :slidesToShow="slidesToShow" :infinite="true" :autoplay="true"
                :autoplaySpeed="4000">
                <div v-for="(img, index) in images" :key="index" class="carousel-card" data-aos="fade-down"
                    data-aos-duration="400" :data-aos-delay="(index + 1) * 300">
                    <a-image :src="img"> </a-image>
                </div>
            </a-carousel>
        </div>


    </div>

</template>

<script setup>
import { ref, onMounted,  } from 'vue';
import { LeftOutlined, RightOutlined } from '@ant-design/icons-vue';
const images = ref([
    slide1, slide2, slide3, slide4, slide5, slide6, slide7, slide8, slide9, slide10, slide11, slide12, slide13, slide14
]);

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

const carousel = ref(null);

const prevSlide = () => {
    carousel.value.prev();
};
const nextSlide = () => {
    carousel.value.next();
};

const slidesToShow = ref(3);

const updateSlidesToShow = () => {
    if (window.innerWidth >= 768) {
        slidesToShow.value = 3;
    } else {
        slidesToShow.value = 2;
    }
};

const next = () => {
    carousel.value.next();
};

const prev = () => {
    carousel.value.prev();
};

onMounted(() => {
    updateSlidesToShow();
    window.addEventListener('resize', updateSlidesToShow);
});
</script>

<style scoped>
.carousel-card {
    padding: 10px;
}

:deep(.carousel-card img) {
    aspect-ratio: 1/1;
    object-fit: cover;
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