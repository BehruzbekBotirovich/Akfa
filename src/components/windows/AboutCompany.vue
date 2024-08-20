<template>

    <!-- about company -->
    <div class="md:flex mb-20">
        <div class="md:w-1/3 relative hovering" @click="ShowVideo = true">
            <img class="w-full h-full object-cover aspect-square covering-img  "
                src="https://www.rehau.com/resource/image/878972/7x5/400/286/6d38342cfbb3403b57585480163395a7/50A14EDDED1D1AD02C7D8B7E8E0AB618/793-d003-cl-1082233.jpg">

            <img class="play-btn" src="./img/PlayBtn.png" alt="">
        </div>
        <div class="lg:flex md:w-2/3 md:p-12 items-center">
            <div class="hidden md:block w-1/2 mr-6 "> <img src="./img/logo.png" width="200" height="120" alt=""> </div>
            <h3 class="font-bold md:hidden py-2">О нас </h3>
            <p class=" flex ">Мы помогаем клиентам подбирать решения, учитывая пожежелания к
                характеристикам окна и
                его стоимости.
                Окно - это объект, которым Вы будете пользоваться много лет, поэтому для нас очень важно, чтобы Вы
                сделали правильный выбор.</p>
        </div>
    </div>

    <!-- about company card-->
    <a-row :gutter="[24, 24]">
        <a-col :xs="24" :md="12" :lg="8" class="flex gap-4  items-center" data-aos="fade-down" data-aos-duration="500"
            data-aos-delay="200">
            <div><img class="icon-img" src="./img/prof1.png" alt=""></div>
            <div style="width: 260px;">
                <h3 class="font-semibold lg:text-lg md:mb-2">Профессионализм</h3>
                <p> Бригада профессиональных мастеров по монтажу и обслуживанию</p>
            </div>
        </a-col>

        <a-col :xs="24" :md="12" :lg="8" class="flex gap-4  items-center" data-aos="fade-down" data-aos-duration="500"
            data-aos-delay="300">
            <div><img class="icon-img" src="./img/prof2.png" alt=""></div>
            <div style="width: 260px;">
                <h3 class="font-semibold lg:text-lg md:mb-2">Ценообразование</h3>
                <p> Лучшие цены на рынке пластиковых окон</p>
            </div>
        </a-col>

        <a-col :xs="24" :md="12" :lg="8" class="flex gap-4 items-center" data-aos="fade-down" data-aos-duration="500"
            data-aos-delay="400">
            <div><img class="icon-img" src="./img/prof3.png" alt=""></div>
            <div style="width: 260px;">
                <h3 class="font-semibold lg:text-lg md:mb-2"> Мобильность </h3>
                <p> Мобильность Заключение договора на дому</p>
            </div>
        </a-col>

        <a-col :xs="24" :sm="12" :lg="8" class="flex gap-4 items-center" data-aos="fade-up" data-aos-duration="500"
            data-aos-delay="200">
            <div><img class="icon-img" src="./img/prof4.png" alt=""></div>
            <div style="width: 260px;">
                <h3 class="font-semibold lg:text-lg md:mb-2">Лояльность </h3>
                <p> 99% клиентов рекомендуют нас своим друзьям</p>
            </div>
        </a-col>

        <a-col :xs="24" :md="12" :lg="8" class="flex gap-4  items-center" data-aos="fade-up" data-aos-duration="500"
            data-aos-delay="300">
            <div><img class="icon-img" src="./img/prof5.png" alt=""></div>
            <div style="max-width: 260px;">
                <h3 class="font-semibold lg:text-lg md:mb-2"> Скорость </h3>
                <p> Короткие сроки установки изделий</p>
            </div>
        </a-col>

        <a-col :xs="24" :md="12" :lg="8" class="flex gap-4 items-center" data-aos="fade-up" data-aos-duration="500"
            data-aos-delay="400">
            <div><img class="icon-img" src="./img/prof6.png" alt=""></div>
            <div style="width: 260px;">
                <h3 class="font-semibold lg:text-lg md:mb-2"> Служба качества </h3>
                <p> Безупречное качество и контроль изделий ПВХ</p>
            </div>
        </a-col>

    </a-row>


    <!-- video ucun -->
    <transition name="slide-fade">
        <video-player v-if="ShowVideo == true" @videoStop="ShowVideo = false"></video-player>
    </Transition>



</template>

<script setup>
import { ref } from 'vue'
import VideoPlayer from '../UI/VideoPlayer.vue'


const ShowVideo = ref(false);
</script>

<style scoped>
.icon-img {
    aspect-ratio: 1/1;

    @media (max-width: 610px) {
        width: 50px;
    }
}

.play-btn {
    position: absolute;
    top: calc(50% - 50px);
    left: calc(50% - 40px);
}

.slide-fade-enter-active {
    transition: all 0.3s ease-out;
}

.slide-fade-leave-active {
    transition: all 0.4s cubic-bezier(1, 0.5, 0.8, 1);
}

.slide-fade-enter-from,
.slide-fade-leave-to {
    transform: translateX(20px);
    opacity: 0;
}

.hovering img {
    cursor: pointer;
    transition: all .3s ease;
}

.hovering:hover .covering-img {

    filter: brightness(80%);
}

.covering-img {
    filter: brightness(90%);
}

.hovering:hover .play-btn {
    scale: 1.1;
}
</style>