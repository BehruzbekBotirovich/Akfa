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
                <h2>Остекление корпоративных объектов</h2>
                <p>Реализуем сложные проекты по остеклению торговых центров,
                    ресторанов, производственных помещений и офисов</p>
            </div>
        </div>
        <!-- info cards -->
        <div class="flex justify-between flex-wrap relative z-10">
            <div class="card-info">
                <div class=""> <img src="./img/window1.png" style=" object-fit: cover; min-width: 80px;"></div>
                <div class="w-3/5">
                    <h1 class="text-lg text-indigo-950 font-semibold    "> Многоквартирные дома</h1>
                    <p class="">

                        Изготовление и монтаж окон ПВХ
                        под ключ. Приглашаем к партнерству
                        застройщиков </p>
                </div>
            </div>
            <div class="card-info">
                <div class=""> <img src="./img/window2.png" style=" object-fit: cover; min-width: 80px;"></div>
                <div class="w-3/5">
                    <h1 class="text-lg text-indigo-950 font-semibold    "> Офисные помещения
                    </h1>
                    <p class="">
                        Установка пластиковых окон,
                        офисных перегородок и
                        дверей и входных групп.
                    </p>
                </div>
            </div>
            <div class="card-info">
                <div class=""> <img src="./img/window3.png" style=" object-fit: cover; min-width: 80px;"></div>
                <div class="w-3/5">
                    <h1 class="text-lg text-indigo-950 font-semibold    "> Социальные объекты</h1>
                    <p class=""> Остекляем детские сады, школы, медицинские учреждения
                    </p>
                </div>
            </div>

            <div class="card-info">
                <div class=""> <img src="./img/window4.png" style=" object-fit: cover; min-width: 80px;"></div>
                <div class="w-3/5">
                    <h1 class="text-lg text-indigo-950 font-semibold    "> Объекты торговли </h1>
                    <p class=""> Способ увеличения площади и объема балкона или лоджии.</p>
                </div>
            </div>

            <div class="card-info">
                <div class=""> <img src="./img/window5.png" style=" object-fit: cover; min-width: 80px;"></div>
                <div class="w-3/5">
                    <h1 class="text-lg text-indigo-950 font-semibold    "> Спортивные объекты
                    </h1>
                    <p class=""> Остекление с крышей
                        Остекляем спортивные залы,
                        бассейны, крытые спорткомплексы</p>
                </div>
            </div>

            <div class="card-info">
                <div class=""> <img src="./img/window6.png" style=" object-fit: cover; min-width: 80px;"></div>
                <div class="w-3/5">
                    <h1 class="text-lg text-indigo-950 font-semibold    "> Производственные помещения</h1>
                    <p class=""> Устанавливаем окна для складских
                        и промышленных зданий в соответствии
                        с требованиями бизнеса</p>
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

import object2 from '@/assets/slide_images/object2.jpg'
import object3 from '@/assets/slide_images/object3.jpg'
import object4 from '@/assets/slide_images/object4.jpg'
import object5 from '@/assets/slide_images/object5.jpg'
import object6 from '@/assets/slide_images/object6.jpg'
import object7 from '@/assets/slide_images/object7.jpg'

const images = ref([
    object4, object2, object3, object5, object6, object7
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
