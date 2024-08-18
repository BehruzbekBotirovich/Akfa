<template>
    <div @click.self="$emit('hideSchyot')" class="fon-dark">
        <a-form :model="form" @submit="handleSubmit"
            class="w-1/3  mx-auto py-6 px-12 bg-my rounded shadow-md relative  " layout="vertical" style="z-index: 3;">
            <h1 class="font-bold text-xl text-center mb-4 flex items-center gap-4 text-white justify-center">
                <ZamerIcon></ZamerIcon>Заказать расчет
            </h1>
            <a-form-item label="Имя" :rules="[{ required: true, message: 'Пожалуйста, введите ваше имя' }]">
                <a-input class="p-4" v-model:value="form.name" placeholder="Введите ваше имя" />
            </a-form-item>

            <a-form-item label="Email"
                :rules="[{ required: true, type: 'email', message: 'Пожалуйста, введите правильный email' }]">
                <a-input class="p-4" v-model:value="form.email" placeholder="Введите ваш email" />
            </a-form-item>

            <a-form-item label="Телефонный номер"
                :rules="[{ required: true, message: 'Пожалуйста, введите ваш телефонный номер' }]">
                <a-input class="p-4" v-model:value="form.phone" placeholder="Введите ваш телефонный номер" />
            </a-form-item>

            <a-form-item class="flex justify-center">
                <button @click="handleSubmit" class="bg-white px-16 py-4 rounded text-lg text-indigo-900 font-bold  ">
                    Заказать расчет
                </button>

            </a-form-item>

        </a-form>
    </div>
</template>

<script setup>
import { reactive } from 'vue';
import ZamerIcon from '../icons/ZamerIcon.vue';
const form = reactive({
    name: '',
    email: '',
    phone: ''
});

const handleSubmit = (e) => {
    e.preventDefault();
    console.log('Форма отправлена:', form);
    message.success('Отзыв успешно оставлен');
    // Здесь можно добавить логику для отправки формы, например, с использованием API
};
</script>

<style scoped>
#app {
    position: relative;
}

.bg-my {
    background-color: #2F2F51;
}

.fon-dark {
    position: fixed;
    z-index: 99;
    width: 100%;
    height: 100vh;
    background: #142c4ca8;
    display: flex;
    align-items: center;
    justify-content: center;

    top: 0;
    display: flex;
    align-items: center;
}

:deep(.ant-form-item-required::before) {
    display: none !important;
}

:deep(.ant-form-item-required) {
    font-size: 18px !important;
    font-weight: 600;
    color: white !important;
}

:deep(.ant-btn >span) {
    color: #EF7F1A;
    font-weight: 700;
}
</style>