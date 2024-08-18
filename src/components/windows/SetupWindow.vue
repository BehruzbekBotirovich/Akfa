<template>
    <div class="window-box ">
        <!-- title carousel -->
        <div class=" flex items-center justify-between">
            <a-carousel ref="carousel" class="carousel">
                <div v-for="img in images" class="carousel-slide">
                    <a-image :src="img" class="carousel-img" />
                </div>
            </a-carousel>
            <div class="text-content">
                <h2>Остекление коттеджей и дач </h2>
                <p> Остекление и отделка под ключ: от коттеджей и дач до террас и беседок. Выделяем личного
                    технолога под каждый объект.</p>

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
                    <h1 class="text-lg text-indigo-950 font-semibold    "> Цветные окна</h1>
                    <p class="">

                        Использование ламинационных окон, ламинации в массе, 3д-ламинации,
                        а также покраска окон. </p>
                </div>
            </div>
            <div class="card-info">
                <div class=""> <img src="./img/window2.png" style=" object-fit: cover; min-width: 80px;"></div>
                <div class="w-3/5">
                    <h1 class="text-lg text-indigo-950 font-semibold    ">Фигурные окна</h1>
                    <p class="">
                        Арочные окна, окна трапеции, треугольные окна, круглые и многоугольные окна
                    </p>
                </div>
            </div>
            <div class="card-info">
                <div class=""> <img src="./img/window3.png" style=" object-fit: cover; min-width: 80px;"></div>
                <div class="w-3/5">
                    <h1 class="text-lg text-indigo-950 font-semibold    "> Алюминиевые конструкции</h1>
                    <p class=""> Идеальный вариант для
                        большой площади остекления: зимние сады, террасы и т.п..
                    </p>
                </div>
            </div>

            <div class="card-info">
                <div class=""> <img src="./img/window4.png" style=" object-fit: cover; min-width: 80px;"></div>
                <div class="w-3/5">
                    <h1 class="text-lg text-indigo-950 font-semibold    "> Деревянные окна
                    </h1>
                    <p class="">
                        Экологичное и натуральное
                        решение для остекления
                        любого объекта.</p>
                </div>
            </div>

            <div class="card-info">
                <div class=""> <img src="./img/window5.png" style=" object-fit: cover; min-width: 80px;"></div>
                <div class="w-3/5">
                    <h1 class="text-lg text-indigo-950 font-semibold    "> Портальные решения</h1>
                    <p class=""> Эксклюзивные дверные и балконные раздвижные
                        конструкции для элитных квартир и респектабельных
                        домов, обеспечивающие панорамный вид
                        и экономящие пространство.</p>
                </div>
            </div>

            <div class="card-info">
                <div class=""> <img src="./img/window6.png" style=" object-fit: cover; min-width: 80px;"></div>
                <div class="w-3/5">
                    <h1 class="text-lg text-indigo-950 font-semibold    "> Рольставни и ворота</h1>
                    <p class=""> Защитные рольставни для частных домов,
                        роллетные ворота.</p>
                </div>
            </div>

        </div>
        <!-- bg -img  -->
        <div class="bg-img">
            <img src="./img/bg3.png" style="width: 100%; height: 100% ; object-fit: cover;">
        </div>

    </div>


</template>

<script setup>
import { ref } from 'vue';
import ZamerIcon from '../icons/ZamerIcon.vue'
import SchyotIcon from '../icons/SchyotIcon.vue'

import dacha1 from '@/assets/slide_images/dacha1.jpg'
import dacha2 from '@/assets/slide_images/dacha2.jpg'
import dacha3 from '@/assets/slide_images/dacha3.jpg'
import dacha4 from '@/assets/slide_images/dacha4.jpg'
import dacha5 from '@/assets/slide_images/dacha5.jpg'
import dacha6 from '@/assets/slide_images/dacha6.jpg'
import dacha7 from '@/assets/slide_images/dacha7.jpg'
import dacha8 from '@/assets/slide_images/dacha8.jpg'



const images = ref([
    dacha6, dacha7, dacha8, dacha1, dacha2, dacha3, dacha4, dacha5
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
