<template>
    <div class="main-container py-12">
        <h1 class="text-indigo-950 text-xl text-center font-semibold mb-4 md:mb-12">Контакты</h1>

        <div class="md:flex ">
            <div class="md:w-1/2 space-y-4 pb-20 px-8 relative">
                <h1 class="text-lg font-semibold">Бесплатная консультация: </h1>
                <div class="flex items-center gap-4 ">
                    <TelIcon></TelIcon>
                    <ul class="flex gap-10 w-full  md:text-xl">
                        <li class="font-bold">{{ telnumber1 }}</li>
                        <li class="font-bold">{{ telnumber2 }}</li>
                    </ul>
                </div>
                <div class="flex items-center gap-5 text-lg">
                    <LocationIcon></LocationIcon> {{ locationtitle }}
                </div>
                <div class="flex items-center gap-5 text-lg">
                    <PochtaIcon></PochtaIcon>{{ email }}
                </div>

                <p class=" md:w-2/5 py-6">Установку должны выполнять только эксперты. Нам доверяют сотни семей.
                    Узнайте поробнее, какие решения вам подходят.
                    Вы можете приобрести недорогие товары
                    при гарантированно
                    высоком качестве.</p>


                <ul class="flex gap-4 icons-media">
                    <li class="rounded-full overflow-hidden w-fit">
                        <a :href=social.tg target="_blank">
                            <TgIcon></TgIcon>
                        </a>
                    </li>

                                        <li>
                        <a :href=social.twit target="_blank"> <img src=" ./icons/twitter.png" width="40" height="40">
                        </a>
                    </li>

                    <li>
                        <a :href=social.facebook target="_blank"> <img src=" ./icons/facebook.png" width="40"
                                height="40">
                        </a>
                    </li>

                    <li>
                        <a :href=social.insta target="_blank"> <img src=" ./icons/insta.png" width="40" height="40">
                        </a>
                    </li>
                </ul>
                <div class="absolute bottom-0  -right-4 w-1/3 md:w-1/2"> <img src="../assets/images/workers.png" alt=""> </div>
            </div>


            <div class="md:w-1/2 py-6  px-8 md:py-12 md:px-20 shadow-2xl">
                <h1 class="text-center text-2xl font-semibold">Остались вопросы?</h1>
                <a-form :model="form" :rules="rules" ref="formRef" layout="vertical" @submit.prevent="submitForm">
                    <a-form-item label="Имя" name="name">
                        <a-input v-model:value="form.name" class=" bg-gray-100 h-12" placeholder="Ваше имя" />
                    </a-form-item>
                    <a-form-item label="Email" name="email">
                        <a-input v-model:value="form.email" class=" bg-gray-100 h-12" placeholder="Ваш email" />
                    </a-form-item>
                    <a-form-item label="Отзыв" name="message">
                        <a-textarea v-model:value="form.message" class=" bg-gray-100  md:pb-12 no-resize"
                            placeholder="Ваш отзыв" rows="4" />
                    </a-form-item>
                    <a-form-item class="flex justify-center">
                        <a-button type="primary" @click="submitForm" html-type="submit"
                            class=" px-10  h-12 bg-indigo-950 ">
                            Отправить сообщение
                        </a-button>
                    </a-form-item>
                </a-form>
            </div>

        </div>
    </div>
</template>

<script setup>
import TelIcon from './icons/TelIcon.vue'
import LocationIcon from './icons/LocationIcon.vue'
import PochtaIcon from './icons/PochtaIcon.vue'
import TgIcon from './icons/TgIcon.vue'
import { ref } from 'vue';
import { message } from 'ant-design-vue';

const formRef = ref(null);
const form = ref({
    name: '',
    email: '',
    message: ''
});

const rules = {
    name: [
        { required: true, message: 'Пожалуйста, введите ваше имя', trigger: 'blur' }
    ],
    email: [
        { required: true, type: 'email', message: 'Пожалуйста, введите корректный email', trigger: ['blur', 'change'] }
    ],
    message: [
        { required: true, message: 'Пожалуйста, введите ваш отзыв', trigger: 'blur', }
    ]
};


const token = '7473538576:AAFh379biNAqPm1g4ToLHkh6Io2aOekDPhU'; // Замените на ваш токен бота
const chatId = '5331352357'; // Замените на ваш chat ID

const submitForm = () => {
    formRef.value.validate()
        .then(() => {
            // Формируем сообщение
            const telegramMessage = `
                Отзыв! \n
                Имя: ${form.value.name}\n
                Email: ${form.value.email}\n
                Отзыв: ${form.value.message}
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
                        message.success('Отзыв успешно отправлен в Telegram');
                    } else {
                        message.error('Ошибка при отправке отзыва');
                    }
                })
                .catch(error => {
                    console.error('Ошибка при отправке в Telegram:', error);
                    message.error('Не удалось отправить отзыв в Telegram');
                });
        })
        .catch(error => {
            console.log('Validation failed:', error);
        });
};

// html data 
const telnumber1 = '+998 94 929 08 02'
const telnumber2 = '+998 94 929 00 00'
const locationtitle = 'qayerdir qayer yerni burchagida '
const email = 'beha@gmail.com'

// social link
const social = {
    tg: 'https://t.me/windowsglass',
    insta: 'https://www.instagram.com/glass_pro.official',
    facebook: '#',
    twit: '#',
}
</script>

<style scoped>
.icons-media>li {
    transition: all .3s ease;
}

.icons-media>li:hover {
    scale: 1.1;

}

.no-resize {
    resize: none;
}

:deep(.ant-form-item-required) {
    font-weight: 600;
    color: #2F2F51;
    font-size: 18px;

}

:deep(.ant-form-item-required::before) {
    display: none !important;
}
</style>
