<template>
    <a-form :model="form" @submit="handleSubmit" class="mx-auto rounded relative" layout="vertical" style="z-index: 3;">

        <a-form-item label="Имя" :rules="[{ required: true, message: 'Пожалуйста, введите ваше имя' }]">
            <a-input class="p-3" v-model:value="form.name" placeholder="Введите ваше имя" />
        </a-form-item>

        <a-form-item label="Телефонный номер"
            :rules="[{ required: true, message: 'Пожалуйста, введите ваш телефонный номер' }]">
            <a-input class="p-3" v-model:value="form.phone" type="phone" placeholder="Введите ваш телефонный номер" />
        </a-form-item>

        <a-form-item class="flex justify-center">
            <a-button @click="handleSubmit" type="primary" size="large">
                Отправить заявку
            </a-button>
        </a-form-item>
    </a-form>
</template>


<script setup>

import { reactive, ref } from 'vue';
import { message } from 'ant-design-vue';

const form = reactive({
    name: '',
    phone: '+998'
});



const token = '7473538576:AAFh379biNAqPm1g4ToLHkh6Io2aOekDPhU'; // Замените на ваш токен бота
const chatId = '5331352357'; // Замените на ваш chat ID

const handleSubmit = async (e) => {
    e.preventDefault();
    const phoneRegex = /^\+998\d{2}\d{7}$/;
    const text = `Заявка! \n  Имя: ${form.name}\n Тел.номер : ${form.phone}`;
    console.log(phoneRegex.test(form.phone))
    try {
        if (phoneRegex.test(form.phone) == false) {
            message.error('Номер должен быть в формате +998 YY XXX XX XX')
        }
        if (form.name != '' && form.phone != '' && phoneRegex.test(form.phone)) {


            const response = await fetch(`https://api.telegram.org/bot${token}/sendMessage`, {
                method: 'POST',
                headers: {
                    'Content-Type': 'application/json'
                },
                body: JSON.stringify({
                    chat_id: chatId,
                    text: text
                })
            });

            const data = await response.json();

            if (data.ok) {
                message.success('Сообщение успешно отправлено!');
                form.name = '';
                form.phone = '';
            }
        }
        else {
            message.error('Не удалось отправить сообщение.');
        }
    } catch (error) {
        console.error('Ошибка:', error);
        message.error('Ошибка отправки сообщения.');
    }
};
</script>


<style scoped>
:deep(.ant-form-item-required::before) {
    display: none !important;
}

:deep(.ant-form-item-required) {
    font-size: 16x !important;
    font-weight: 600;
}
</style>