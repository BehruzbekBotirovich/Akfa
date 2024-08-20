<template>
    <div class="relative py-8 mb-4 shadow-lg">
        <a-carousel :dots="false" :slides-to-show="slidesToShow" :infinite="true" draggable :autoplay="false"
            ref="carousel">
            <div v-for="(img, index) in images" :key="index" class="img-container">
                <img :src="img.src" :alt="img.alt" class="rasm" />
            </div>
        </a-carousel>

        <!-- Кнопки навигации -->
        <button @click="prev" class="prev">
            <LeftOutlined />
        </button>

        <button @click="next" class="next">
            <RightOutlined />
        </button>
    </div>
</template>

<script setup>
import { ref, onMounted } from 'vue';
import { LeftOutlined, RightOutlined } from '@ant-design/icons-vue'
const images = ref([
    { src: 'https://via.placeholder.com/595x842.png?text=serficate+1', alt: 'Sertificate 1' },
    { src: 'https://via.placeholder.com/595x842.png?text=serficate+2', alt: 'Sertificate 2' },
    { src: 'https://via.placeholder.com/595x842.png?text=serficate+3', alt: 'Sertificate 3' },
    { src: 'https://via.placeholder.com/595x842.png?text=serficate+4', alt: 'Sertificate 4' },
    { src: 'https://via.placeholder.com/595x842.png?text=serficate+5', alt: 'Sertificate 5' },
]);

const slidesToShow = ref(4);
const carousel = ref(null);

const updateSlidesToShow = () => {
    if (window.innerWidth >= 768) {
        slidesToShow.value = 4;
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
.rasm {
    width: 100%;
    height: auto;
    object-fit: cover;
}

.img-container {
    padding: 0 10px;
}

.prev {
    position: absolute;
    top: 50%;
    left: -40px;
    transform: translateY(-50%);
    background: transparent;
    border: none;
    cursor: pointer;
    font-size: 40px;
    padding: 0 10px;

    @media (max-width:610px) {
        top: calc(100% + 20px);
        left: 40%;

    }
}

.next {
    position: absolute;
    top: 50%;
    right: -40px;
    transform: translateY(-50%);
    background: transparent;
    border: none;
    cursor: pointer;
    font-size: 40px;

    @media (max-width:610px) {
        top: calc(100% + 20px);
        right: 40%;
    }
}

.next:hover,
.prev:hover {
    color: #f97316;
    transition: all 0.2s ease-in;
}
</style>