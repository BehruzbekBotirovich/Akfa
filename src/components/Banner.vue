<template>
    <div class="bg-div relative mt-20">
        <div class="darking"></div>
        <div class="main-container lg:flex gap-12 items-center justify-between">

            <!-- addффф -->
            <div class="content relative lg:w-1/2 mb-2" style="z-index: 3;">
                <h1 data-aos="fade-right" data-aos-duration="500" data-aos-delay="200"
                    class="text-bold text-4xl text-cyan-200">Glass Pro -</h1>
                <p data-aos="fade-right" data-aos-duration="500" data-aos-delay="200"
                    class="sm:text-2xl lg:text-5xl font-semibold text-white"> Профессиональный подход к остеклению</p>
                <div class="flex justify-between gap-4  sm:mt-6 lg:mt-12">
                    <div data-aos="fade-up" data-aos-duration="500" data-aos-delay="200">
                        <Sloy1Icon></Sloy1Icon>
                        <p class="text-white  xl:w-48 ml-4 mt-2">Современные окна и балконные конструкции по доступным
                            ценам
                        </p>
                    </div>
                    <div data-aos="fade-up" data-aos-duration="500" data-aos-delay="300">
                        <Sloy2Icon></Sloy2Icon>
                        <p class="text-white  xl:w-48 ml-2 mt-2">Современные окна и балконные конструкции по доступным
                            ценам
                        </p>
                    </div>
                    <div data-aos="fade-up" data-aos-duration="500" data-aos-delay="400">
                        <Sloy3Icon></Sloy3Icon>
                        <p class="text-white  xl:w-48 mt-2">Современные окна и балконные конструкции по доступным ценам
                        </p>
                    </div>

                </div>
            </div>

            <!-- форма -->
            <div class="relative z-10 bg-white   p-4 md:px-16 md:pt-10 md:pb-4 lg:w-1/3  rounded-xl" data-aos="fade-left"
                data-aos-duration="500" data-aos-delay="200">
                <h1 class="font-bold text-lg text-center">Вызвать замерщика</h1>
                <a-form :model="form" :rules="rules" ref="formRef" layout="vertical" @submit.prevent="submitForm">
                    <a-form-item label="Имя" name="name">
                        <a-input v-model:value="form.name" class="bg-gray-100 h-12" placeholder="Ваше имя" />
                    </a-form-item>
                    <a-form-item label="Email" name="email">
                        <a-input v-model:value="form.email" class="bg-gray-100 h-12" placeholder="Ваш email" />
                    </a-form-item>
                    <a-form-item label="Телефон" name="tel">
                        <a-input v-model:value="form.tel" class="bg-gray-100 h-12" placeholder="Ваш номер телефона" />
                    </a-form-item>
                    <a-form-item class="flex justify-center ">
                        <a-button type="primary" @click="submitForm" html-type="submit" class="mt-4 px-10 h-12">
                            Отправить сообщение
                        </a-button>
                    </a-form-item>
                </a-form>
            </div>

        </div>
    </div>
</template>

<script setup>
import { ref } from 'vue';
import { message } from 'ant-design-vue'; //Импортируем уведомления

import Sloy1Icon from '../components/icons/Sloy1Icon.vue'
import Sloy2Icon from '../components/icons/Sloy2Icon.vue'
import Sloy3Icon from '../components/icons/Sloy3Icon.vue'



const formRef = ref(null);
const form = ref({
    name: '',
    email: '',
    tel: '+998'
});

const rules = {
    name: [
        { required: true, message: 'Пожалуйста, введите ваше имя', trigger: 'blur' }
    ],
    email: [
        { required: true, type: 'email', message: 'Пожалуйста, введите корректный email', trigger: ['blur', 'change'] }
    ],
    tel: [
        { required: true, message: 'Пожалуйста, введите ваш номер', trigger: 'blur' },
        {
            validator: (rule, value) => {
                const regex = /^\+998\d{9}$/;
                if (!value) {
                    return Promise.reject('Пожалуйста, введите ваш номер');
                } else if (!regex.test(value)) {
                    return Promise.reject('Номер должен быть в формате +998XXXXXXXXX');
                } else {
                    return Promise.resolve();
                }
            },
            trigger: 'blur'
        },
    ],
};

const token = '7473538576:AAFh379biNAqPm1g4ToLHkh6Io2aOekDPhU'; // Замените на ваш токен бота
const chatId = '5331352357'; // Замените на ваш chat ID

const submitForm = () => {
    formRef.value.validate()
        .then(() => {
            // Формируем сообщение
            const telegramMessage = `
        Заявка! \n
        Имя: ${form.value.name}\n
        Email: ${form.value.email}\n
        Номер: ${form.value.tel}
      `;

            // Отправляем запрос в Telegram API
            fetch(`https://api.telegram.org/bot${token}/sendMessage`, {
                method: 'POST',
                headers: {
                    'Content-Type': 'application/json'
                },
                body: JSON.stringify({
                    chat_id: chatId,
                    text: telegramMessage
                })
            })
                .then(response => response.json())
                .then(data => {
                    if (data.ok) {
                        message.success('Отзыв успешно отправлен');
                        form.value.name = '';
                        form.value.email = '';
                        form.value.tel = '+998';
                    } else {
                        message.error('Ошибка при отправке отзыва');
                    }
                })
                .catch(error => {
                    console.error('Ошибка при отправке ', error);
                    message.error('Не удалось отправить отзыв ');
                });
        })
        .catch(error => {
            console.log('Validation failed:', error);
        });
};

</script>

<style scoped>
.bg-div {
    padding: 60px 0;
    width: 100%;
    background-repeat: no-repeat;
    background-size: cover;
    background-image: url('../assets/images/bg.webp');
}


.darking {
    z-index: 1;
    position: absolute;
    width: 100%;
    height: 100%;
    background: rgba(0, 0, 0, 0.3);
    top: 0;
    left: 0;
}

:deep(.ant-form-item-required::before) {
    display: none !important;
}

:deep(.ant-form-item) {
    @media (max-width:1024px) {
        margin-bottom: 14px;
    }
}

:deep(.ant-menu-horizontal) {
    border-bottom: none;
}

.content {
    position: relative;
    /* Установлено position: relative */
}
</style>
