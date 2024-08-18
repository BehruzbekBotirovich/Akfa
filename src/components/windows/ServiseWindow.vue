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
                <h2>Установка пластиковых окон</h2>
                <p>Пластиковые окна Akfa от проверенного производителя с гарантией качества</p>
                <div class="flex gap-4">
                    <a-button type="primary" @click="showZamer = true"
                        class="flex items-center gap-2  justify-center h-12 rounded font-semibold text-white bg-orange-500">
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
                    <h1 class="text-lg text-indigo-950 font-semibold    ">Пластиковые окна </h1>
                    <p class="">Использование ламинационных окон, ламинации в массе, 3д-ламинации, а также покраска
                        окон.
                    </p>
                </div>
            </div>
            <div class="card-info">
                <div class=""> <img src="./img/window2.png" style=" object-fit: cover; min-width: 80px;"></div>
                <div class="w-3/5">
                    <h1 class="text-lg text-indigo-950 font-semibold    ">Ламинация Пластиковые </h1>
                    <p class=""> окна могут быть любого нужного вам цвета. Внутри и снаружи.
                    </p>
                </div>
            </div>
            <div class="card-info">
                <div class=""> <img src="./img/window3.png" style=" object-fit: cover; min-width: 80px;"></div>
                <div class="w-3/5">
                    <h1 class="text-lg text-indigo-950 font-semibold    ">Подоконники </h1>
                    <p class="">
                        Качественный подоконник не царапается, выдерживает большие нагрузки и будет служить вам долгие
                        годы.
                    </p>
                </div>
            </div>

            <div class="card-info">
                <div class=""> <img src="./img/window4.png" style=" object-fit: cover; min-width: 80px;"></div>
                <div class="w-3/5">
                    <h1 class="text-lg text-indigo-950 font-semibold    "> Цветные ручки </h1>
                    <p class=""> Оригинальные оконные ручки подчеркнут дизайн окна. Подберем оптимальный цвет ручек в
                        зависимости
                        от цвета всей конструкции.</p>
                </div>
            </div>

            <div class="card-info">
                <div class=""> <img src="./img/window5.png" style=" object-fit: cover; min-width: 80px;"></div>
                <div class="w-3/5">
                    <h1 class="text-lg text-indigo-950 font-semibold    ">Проветривател</h1>
                    <p class=""> Постоянное обновление воздуха
                        в комнате снижает риск аллергии, улучшает сон и благоприятно влияет
                        на самочувствие. </p>
                </div>
            </div>

            <div class="card-info">
                <div class=""> <img src="./img/window6.png" style=" object-fit: cover; min-width: 80px;"></div>
                <div class="w-3/5">
                    <h1 class="text-lg text-indigo-950 font-semibold    "> Москитные сетки</h1>
                    <p class=""> Нежеланные насекомые останутся
                        на улице, а ваша кошка - в квартире. Устанавливаем сетки для пластиковых окон любых форм и
                        размеров.</p>
                </div>
            </div>

        </div>
        <!-- bg -img  -->
        <div class="bg-img">
            <img src="./img/bg2.png" style="width: 100%; height: 100% ; object-fit: cover;">
        </div>

    </div>


</template>

<script setup>
import { ref } from 'vue';
import ZamerIcon from '../icons/ZamerIcon.vue'
import SchyotIcon from '../icons/SchyotIcon.vue'
import oyna1 from '@/assets/slide_images/oyna1.jpg'
import oyna2 from '@/assets/slide_images/oyna2.jpg'
import oyna3 from '@/assets/slide_images/oyna3.jpg'
import oyna4 from '@/assets/slide_images/oyna4.jpg'
import oyna5 from '@/assets/slide_images/oyna5.jpg'
import oyna6 from '@/assets/slide_images/oyna6.jpg'

const images = ref([
    oyna1, oyna2, oyna3, oyna4, oyna5, oyna6
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

:deep(.ant-modal-content) {
    overflow: hidden;
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
