<template>
    <header class="fixed top-0 left-0 z-20 bg-white w-full shadow-md">
        <div class="flex gap-10 py-4 main-container justify-between">
            <div><img src="../assets/images/logo.png" width="60" height="60"></div>

            <!-- Desktop Menu -->
            <a-menu mode="horizontal" class="items-center hidden lg:block" style="width: 520px;">
                <!-- Menu items go here -->
                <a-menu-item :class="{ activeItem: activeSection === 'about-us' }" key="1">
                    <a @click.prevent="scrollTo('about-us')" href="#">Услуги</a>
                </a-menu-item>
                <a-menu-item :class="{ activeItem: activeSection === 'product' }" key="2">
                    <a @click.prevent="scrollTo('product')" href="#">Продукция</a>
                </a-menu-item>
                <a-menu-item :class="{ activeItem: activeSection === 'workings' }" key="3">
                    <a @click.prevent="scrollTo('workings')" href="#">О компании</a>
                </a-menu-item>
                <a-menu-item :class="{ activeItem: activeSection === 'faq' }" key="4">
                    <a @click.prevent="scrollTo('faq')" href="#">Вопрос-ответ</a>
                </a-menu-item>
                <a-menu-item :class="{ activeItem: activeSection === 'contact' }" key="5">
                    <a @click.prevent="scrollTo('contact')" href="#">Контакты</a>
                </a-menu-item>

            </a-menu>

            <!-- Burger Icon for Mobile -->
            <div class="lg:hidden">
                <a-button type="ghost" @click="showMobileMenu = !showMobileMenu" class="flex items-center text-xl">
                    <MenuUnfoldOutlined :class="showMobileMenu ? 'rotating' : 'inactive-class'" />
                </a-button>
            </div>

            <!-- Desktop buttons -->
            <div class="hidden lg:flex gap-4 w-fit">
                <a-button type="" @click="showModal"
                    class="flex items-center gap-2 h-10 rounded font-semibold text-white bg-orange-500">
                    <ZamerIcon></ZamerIcon> Оставить заявку
                </a-button>
            </div>
        </div>

        <!-- Mobile Menu -->
        <Transition name="slide-fade">
            <a-menu v-if="showMobileMenu" mode="vertical"
                class="lg:hidden fixed top-0 left-0 w-3/4 z-10 h-screen bg-white shadow-lg">
                <!-- Menu items go here -->

                <a-menu-item :class="{ active: activeSection === 'about-us' }" key="1">
                    <a @click.prevent="scrollTo('about-us')" href="#">Услуги</a>
                </a-menu-item>
                <a-menu-item :class="{ active: activeSection === 'product' }" key="2">
                    <a @click.prevent="scrollTo('product')" href="#">Продукция</a>
                </a-menu-item>
                <a-menu-item :class="{ active: activeSection === 'workings' }" key="3">
                    <a @click.prevent="scrollTo('workings')" href="#">О компании</a>
                </a-menu-item>
                <a-menu-item :class="{ active: activeSection === 'faq' }" key="4">
                    <a @click.prevent="scrollTo('faq')" href="#">Вопрос-ответ</a>
                </a-menu-item>
                <a-menu-item :class="{ active: activeSection === 'contact' }" key="5">
                    <a @click.prevent="scrollTo('contact')" href="#">Контакты</a>
                </a-menu-item>

            </a-menu>
        </Transition>

        <a-modal v-model:open="open" title="Вызвать замерщика на дом" @ok="handleOk" :footer="false">
            <ZamerWindow></ZamerWindow>
        </a-modal>
    </header>



</template>
<script setup>
import ZamerIcon from './icons/ZamerIcon.vue'
import ZamerWindow from './windows/ZamerWindow.vue'
import { ref, onMounted, onUnmounted } from 'vue';
import { MenuUnfoldOutlined, MenuFoldOutlined } from '@ant-design/icons-vue';
const activeSection = ref('');
const showMobileMenu = ref(false); // State to show/hide mobile menu

// moldalka ant vue
const open = ref(false);
const showModal = () => {
    open.value = true;
};
const handleOk = e => {
    console.log(e);
    open.value = false;
};

// menu boyicha navigatsiya scroll boyicha
const scrollTo = (elementId) => {
    const element = document.getElementById(elementId);
    showMobileMenu.value = false;
    if (element) {
        element.scrollIntoView({ behavior: 'smooth' });
        activeSection.value = elementId;
    }
};

const handleScroll = () => {
    const sections = ['about-us', 'product', 'workings', 'faq', 'contact'];
    const scrollPosition = window.scrollY + window.innerHeight / 2;

    for (const section of sections) {
        const element = document.getElementById(section);
        if (element) {
            const { offsetTop, offsetHeight } = element;
            if (scrollPosition >= offsetTop && scrollPosition < offsetTop + offsetHeight) {
                activeSection.value = section;
                break;
            }
        }
    }
};

onMounted(() => {
    window.addEventListener('scroll', handleScroll);
    handleScroll(); // To set the active section on initial load
});

onUnmounted(() => {
    window.removeEventListener('scroll', handleScroll);
});
</script>
<style scoped>
.activeItem>span>a {
    color: blue;
    padding-bottom: 13px;
    border-bottom: 2px solid blue;
    transition: all 0.2s easy;
}


:deep(.ant-menu-horizontal) {
    border-bottom: none;
}

:deep(.ant-menu-item-selected) {
    color: black !important;

}

:deep(.ant-menu-item-selected::after) {
    display: none;
}

/* Transition for Mobile Menu */
.slide-fade-enter-active,
.slide-fade-leave-active {
    transition: transform 0.3s ease, opacity 0.3s ease;
}

.slide-fade-enter-from,
.slide-fade-leave-to {
    transform: translateX(-100%);
    opacity: 0;
}

.v-enter-active,
.v-leave-active {
    transition: opacity 0.5s ease;
}

.v-enter-from,
.v-leave-to {
    opacity: 0;
}

.rotating {
    transform: rotate(180deg);
}
</style>
