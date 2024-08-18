<template>

    <!-- about company -->
    <div class="flex mb-20">
        <div class="lg:flex w-1/2 p-12">
            <div class=" lg:w-1/2 "> <img src="./img/logo.png" width="200" height="120" alt=""> </div>
            <p class=" lg:w-1/2 flex items-end">Мы помогаем клиентам подбирать решения, учитывая пожежелания к
                характеристикам окна и
                его стоимости.
                Окно - это объект, которым Вы будете пользоваться много лет, поэтому для нас очень важно, чтобы Вы
                сделали правильный выбор.</p>
        </div>
        <div class="w-1/2 relative hovering" @click="ShowVideo = true">
            <img class="w-full h-full object-cover covering-img "
                src="https://s3-alpha-sig.figma.com/img/4f2c/c634/15febc71f053d01cb88bd8ea5a8c2bfc?Expires=1722816000&Key-Pair-Id=APKAQ4GOSFWCVNEHN3O4&Signature=WOn5c0CMXvL3LaDCR09YEH0IxJ7rVah4vWekPE15hkGPXDAm8IzKFOsrJCT~HzQGd0GGHGBpRQcu5gIGTTklQ6HXwaKrugZquAV0V~FPOKYPH1ECpMC1Rqc6EvujrRVCR0GSC9tkVzoMxIAC7j8oTPbmW-g7S0YbuXWoD69KmANmY0CksK-EP30h3RbxMV0GWKUKIkysZ02u3RcpqGUrBechHjEgZ72sUGlQAPwzbHxIsyT6DYhPLQwcZE2LxtR2dWgnwEao3aKjuwajLn9yyXVZJ6wfUKk3TWExfUcGx54VwfWiYZCq~067-zJeQLEw1nGdVUWWbTjby9wOOlDdWA__"
                alt="">

            <img class="play-btn" src="./img/PlayBtn.png" alt="">
        </div>
    </div>

    <!-- about company card-->
    <a-row :gutter="[24, 24]" data-aos="zoom-in" data-aos-delay="200">
        <a-col :xs="24" :md="12" :lg="8" class="flex gap-4  items-center" data-aos="zoom-in" data-aos-delay="200">
            <div><img class="icon-img" src="./img/prof1.png" alt=""></div>
            <div style="width: 260px;">
                <h3 class="font-semibold lg:text-lg md:mb-2">Профессионализм</h3>
                <p> Бригада профессиональных мастеров по монтажу и обслуживанию</p>
            </div>
        </a-col>

        <a-col :xs="24" :md="12" :lg="8" class="flex gap-4  items-center">
            <div><img class="icon-img" src="./img/prof2.png" alt=""></div>
            <div style="width: 260px;">
                <h3 class="font-semibold lg:text-lg md:mb-2">Ценообразование</h3>
                <p> Лучшие цены на рынке пластиковых окон</p>
            </div>
        </a-col>

        <a-col :xs="24" :md="12" :lg="8" class="flex gap-4 items-center">
            <div><img class="icon-img" src="./img/prof3.png" alt=""></div>
            <div style="width: 260px;">
                <h3 class="font-semibold lg:text-lg md:mb-2"> Мобильность </h3>
                <p> Мобильность Заключение договора на дому</p>
            </div>
        </a-col>

        <a-col :xs="24" :sm="12" :lg="8" class="flex gap-4 items-center">
            <div><img class="icon-img" src="./img/prof4.png" alt=""></div>
            <div style="width: 260px;">
                <h3 class="font-semibold lg:text-lg md:mb-2">Лояльность </h3>
                <p> 99% клиентов рекомендуют нас своим друзьям</p>
            </div>
        </a-col>

        <a-col :xs="24" :md="12" :lg="8" class="flex gap-4  items-center">
            <div><img class="icon-img" src="./img/prof5.png" alt=""></div>
            <div style="max-width: 260px;">
                <h3 class="font-semibold lg:text-lg md:mb-2"> Скорость </h3>
                <p> Короткие сроки установки изделий</p>
            </div>
        </a-col>

        <a-col :xs="24" :md="12" :lg="8" class="flex gap-4 items-center">
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

.hovering:hover .play-btn {
    scale: 1.1;
}
</style>