<template>

    <h1 class="text-3xl text-center mb-12 mt-8 font-semibold text-gray-800">Продукции</h1>
    <ProductsSlider></ProductsSlider>
    <div class="bg-img my-container mb-14 relative">
        <div class="main-container  relative  ">
            <div class="relative text-white  mb-16" style="z-index: 2;">
                <h1 class=" text-lg md:text-5xl font-extrabold text-center tracking-widest">AKFA</h1>
                <p class="text-center  md:text-2xl">гарантия качества</p>
            </div>


            <div class=" md:flex  space-y-2   justify-around relative gap-2 boxs" style="z-index: 2;">
                <div data-aos="fade-down" data-aos-duration="500" data-aos-delay="200">
                    <div class="flex justify-center"><img src="../assets/images/Sloy01.png" alt=""></div>
                    <h3 class="text-white text-center  w-28">Сертифицированный производитель AKFA </h3>
                </div>

                <div data-aos="fade-down" data-aos-duration="500" data-aos-delay="300">
                    <div class="flex justify-center"><img src="../assets/images/Sloy02.png" alt=""></div>
                    <h3 class="text-white text-center  w-28">Инновационный
                        оконный завод</h3>
                </div>
                <div data-aos="fade-down" data-aos-duration="500" data-aos-delay="400">
                    <div class="flex justify-center"><img src="../assets/images/Sloy03.png" alt=""></div>
                    <h3 class="text-white text-center   w-28">Лидер по переработке
                        профилей в Узбекистане</h3>
                </div>
                <div data-aos="fade-down" data-aos-duration="500" data-aos-delay="500">
                    <div class="flex justify-center"><img src="../assets/images/Sloy04.png" alt=""></div>
                    <h3 class="text-white text-center  w-28">Высокотехнологичное
                        автоматизированное
                        оборудование</h3>
                </div>

                <div data-aos="fade-down" data-aos-duration="500" data-aos-delay="600">
                    <div class="flex justify-center  "><img src="../assets/images/Sloy05.png" alt=""></div>
                    <h3 class="text-white text-center w-28">Широкий
                        ассортимент продукции</h3>
                </div>
            </div>

        </div>
        <div class="blue-drop"> </div>
    </div>


    <div class="flex justify-center">
        <a-button type="primary" @click="showModal"
            class="flex items-center gap-4 px-8  h-14 rounded font-semibold text-white bg-indigo-900">
            <SchyotIcon></SchyotIcon> Заказать расчет
        </a-button>
        <a-modal v-model:open="open" title="Оставьте заявку" :footer="false" @ok="handleOk">
            <ZamerWindow></ZamerWindow>
        </a-modal>
    </div>


</template>

<script setup>
import ProductsSlider from './Products.vue'
import SchyotIcon from './icons/SchyotIcon.vue'
import ZamerWindow from './windows/ZamerWindow.vue';
import { ref } from 'vue';

const open = ref(false);
const showModal = () => {
    open.value = true;
};
const handleOk = e => {
    console.log(e);
    open.value = false;
};
</script>

<style scoped>
.bg-img {
    position: relative;
    width: 100%;
    height: 100%;
    padding: 30px 70px 80px 70px;
    background-image: url('../assets/images/bg2.jpg');
    background-repeat: no-repeat;
    background-size: cover;

    @media(max-width:610px) {
        padding: 10px 30px 20px 30px;
    }
}

@media (max-width:610px) {
    .boxs>div {
        display: flex;
        align-items: center;
        gap: 10px;

        img {
            width: 60px;
        }
    }

    .boxs>div:nth-child(even) {
        margin-left: 80px;
    }


}




.blue-drop {
    position: absolute;
    top: 0;
    left: 0;
    z-index: 1;
    width: 100%;
    height: 100%;
    background: rgba(8, 8, 48, 0.811);
}
</style>