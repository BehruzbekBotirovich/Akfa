<template>
    <div class="main-container mt-12">
        <a-collapse v-model:activeKey="activeKey" accordion>
            <h1 class="text-white text-2xl font-semibold text-center mb-4 md:mb-10">Вопрос-ответ</h1>

            <a-collapse-panel v-for="item in SavolJavob " :header=item.savol>
                <p>{{ item.javob }}</p>
            </a-collapse-panel>


        </a-collapse>
    </div>

</template>
<script lang="ts" setup>
import { ref } from 'vue';
const activeKey = ref([]);
const SavolJavob = [
    {
        savol: 'bu yerda kop beriladigan savol yoki klientlar berishi mumkin bolgan savol bolishi kerak ',
        javob: 'bu yerda javobi '
    },
    {
        savol: 'bu yerda kop beriladigan savol yoki klientlar berishi mumkin bolgan savol bolishi kerak ',
        javob: 'bu yerda javobi '
    }, {
        savol: 'bu yerda kop beriladigan savol yoki klientlar berishi mumkin bolgan savol bolishi kerak ',
        javob: 'bu yerda javobi '
    }, {
        savol: 'bu yerda kop beriladigan savol yoki klientlar berishi mumkin bolgan savol bolishi kerak ',
        javob: 'bu yerda javobi '
    },

]

</script>

<style scoped>
:deep(.ant-collapse) {
    padding: 50px;
    background: #EF7F1A;

    @media (max-width:610px) {
        padding: 20px;
    }
}

:deep(.ant-collapse-item) {
    background: white;
    margin-bottom: 10px;
    border-radius: 5px !important;
    padding: 10px;

    @media (max-width:610px) {
        padding: 6px;
    }
}

:deep(.ant-collapse-header-text) {
    font-size: 18px;
    font-weight: 700;

    @media (max-width:610px) {
        font-size: 14px;
    }
}

:deep(.ant-collapse-header-text:hover) {
    color: orange;
}



:deep(.ant-collapse-expand-icon) {
    position: absolute;
    right: 0px;
}

:deep(.ant-collapse-content) {
    border: none;
    background-color: transparent;

}

:deep(.ant-collapse-header) {
    padding-bottom: 0px !important;
}

:deep(.ant-collapse-content-box) {
    background-color: transparent;
    font-size: 16px;
    font-weight: 400;
    line-height: 18.75px;

}

:deep(.ant-collapse-expand-icon) {
    scale: 2
}

:deep(.ant-collapse-item:hover .ant-collapse-expand-icon path) {
    fill: orange;
}
</style>