<template>
    <div class="window-box ">
        <!-- title carousel -->
        <div class=" flex items-center justify-between">
            <a-carousel ref="carousel" class="carousel">
                <div v-for="img in images" :key="index" class="carousel-slide">
                    <a-image :src="img" class="carousel-img" />
                </div>
            </a-carousel>
            <div class="text-content">
                <h2>Остекление балконов и лоджий </h2>
                <p>Занимаемся остеклением и отделкой балконов и лоджий. Теплое и холодное остекление, изготовление
                    выносов и крыш. Беремся за сложные объекты</p>

                <div class="flex gap-4">
                    <a-button type="primary" @click="showZamer = true"
                        class="flex items-center gap-2  w-1/2 justify-center h-12 rounded font-semibold text-white bg-orange-500">
                        <ZamerIcon></ZamerIcon> Заявка на замер
                    </a-button>
                </div>
            </div>
        </div>
        <!-- info cards -->
        <div class="flex justify-between flex-wrap relative z-10">
            <div class="card-info">
                <div class=""> <img src="./img/window1.png" style=" object-fit: cover; min-width: 80px;"></div>
                <div class="w-3/5">
                    <h1 class="text-lg text-indigo-950 font-semibold    ">Тёплое остекление</h1>
                    <p class="">
                        Теплое остекление — возможность сделать из балкона или лоджии полноценное жилое помещение.
                    </p>
                </div>
            </div>
            <div class="card-info">
                <div class=""> <img src="./img/window2.png" style=" object-fit: cover; min-width: 80px;"></div>
                <div class="w-3/5">
                    <h1 class="text-lg text-indigo-950 font-semibold    ">Холодное остекление</h1>
                    <p class="">
                        Холодное остекление рекомендовано в случаях, когда балкон или лоджия используются для хранения
                        вещей.
                    </p>
                </div>
            </div>
            <div class="card-info">
                <div class=""> <img src="./img/window3.png" style=" object-fit: cover; min-width: 80px;"></div>
                <div class="w-3/5">
                    <h1 class="text-lg text-indigo-950 font-semibold    ">Панорамное остекление </h1>
                    <p class=""> Остекление от пола до потолка, дающее максимальное естественное освещение
                        и прекрасный обзор окрестностей.
                    </p>
                </div>
            </div>

            <div class="card-info">
                <div class=""> <img src="./img/window4.png" style=" object-fit: cover; min-width: 80px;"></div>
                <div class="w-3/5">
                    <h1 class="text-lg text-indigo-950 font-semibold    ">Остекление с выносом </h1>
                    <p class="">
                        Способ увеличения площади и объема балкона или лоджии.</p>
                </div>
            </div>

            <div class="card-info">
                <div class=""> <img src="./img/window5.png" style=" object-fit: cover; min-width: 80px;"></div>
                <div class="w-3/5">
                    <h1 class="text-lg text-indigo-950 font-semibold    ">Остекление с крышей</h1>
                    <p class=""> Остекление с крышей
                        Строительство крыши для домов
                        с высоким потолком и квартир, расположенных на последних этажах.</p>
                </div>
            </div>

            <div class="card-info">
                <div class=""> <img src="./img/window6.png" style=" object-fit: cover; min-width: 80px;"></div>
                <div class="w-3/5">
                    <h1 class="text-lg text-indigo-950 font-semibold    "> Объединение с комнатой</h1>
                    <p class=""> Объединение с комнатой Перепланировка квартиры, дающая дополнительные метры полезной
                        площади и улучшающая жилищные
                        условия.</p>
                </div>
            </div>

        </div>
        <!-- bg -img  -->
        <div class="bg-img">
            <img src="./img/image1.png" style="width: 100%; height: 100% ; object-fit: cover;">
        </div>

    </div>


</template>

<script setup>
import { ref } from 'vue';
import ZamerIcon from '../icons/ZamerIcon.vue'

import balkon1 from '@/assets/slide_images/steklo1.jpg'
import balkon2 from '@/assets/slide_images/steklo2.jpg'
import balkon3 from '@/assets/slide_images/steklo3.jpg'
import balkon4 from '@/assets/slide_images/steklo4.jpg'
import balkon5 from '@/assets/slide_images/steklo5.jpg'
import balkon6 from '@/assets/slide_images/steklo6.jpg'
import balkon7 from '@/assets/slide_images/steklo7.jpg'


const images = ref([
    balkon1, balkon2, balkon3, balkon4, balkon5, balkon6, balkon7
]);

const carousel = ref(null);
</script>

<style scoped>
.window-box {
    border-radius: 0.5rem;
    position: relative;
    padding: 0 10px 0 10px;
}

.bg-img {
    z-index: 3;
    width: 50%;
    overflow: hidden;
    position: absolute;
    bottom: -20px;
    right: -24px;
    border-radius: 0 0 0.5rem 0;
}

.card-info {
    width: 50%;
    display: flex;
    align-items: center;
    gap: 24px;
    margin-bottom: 30px;
}


.carousel {
    width: 40%;
}

.carousel-slide {
    display: flex;
    justify-content: center;
    align-items: center;
}

:deep(.carousel-img) {
    width: 100%;
    aspect-ratio: 5/3;
    object-fit: cover;
}


.text-content {
    width: 50%;
    padding: 20px 40px 60px 20px;
}

.text-content h2 {
    font-size: 24px;
    font-weight: 700;
    line-height: 28.13px;
    margin-bottom: 20px;
}

.text-content p {
    width: 80%;
    font-size: 18px;
    line-height: 28.13px;
    margin-bottom: 20px;
}
</style>
