<template>
    <div class="relative py-8 shadow-lg">
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
                    <div v-for="(img, index) in images" :key="index" class="img-container">
                        <img :src="img.src" :alt="img.alt" class=" rasm">
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

        <!-- map -->
        <div>
        </div>



    </div>
</template>
<script setup>
import { ref } from 'vue';

const images = ref([
    { src: 'https://via.placeholder.com/200x200.png?text=serficate+3', alt: 'Sertificate 3' },
    { src: 'https://via.placeholder.com/200x200.png?text=serficate+4', alt: 'Sertificate 4' },
    { src: 'https://via.placeholder.com/200x200.png?text=serficate+5', alt: 'Sertificate 5' },
    { src: 'https://via.placeholder.com/200x200.png?text=serficate+6', alt: 'Sertificate 6' },
    { src: 'https://via.placeholder.com/200x200.png?text=serficate+7', alt: 'Sertificate 7' },
]);

const currentIndex = ref(0);

const next = () => {
    if (currentIndex.value < images.value.length - 4) {
        currentIndex.value++;
    }
};

const prev = () => {
    if (currentIndex.value > 0) {
        currentIndex.value--;
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

.rasm {
    width: 15rem;
    height: 15rem;
    object-fit: cover;
}

.carousel-track {
    display: flex;
    transition: transform 0.3s ease-in-out;
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