<script setup>
import { RouterLink, RouterView } from 'vue-router'
import HeaderMain from './components/HeaderMain.vue'
import Banner from './components/Banner.vue'
import AboutUs from './components/AboutUs.vue'

import AboutProduct from './components/AboutProduct.vue'
import Workings from './components/Workings.vue'
import Portfolio from './components/Portfolio.vue'
import FaqAsk from './components/FaqAsk.vue'
import ContactUs from './components/ContactUs.vue'
import FooterEnd from './components/FooterEnd.vue'
import Map from './components/Map.vue'
</script>

<template>

    <HeaderMain></HeaderMain>
    <Banner />
    <div id="about-us">
        <AboutUs></AboutUs>
    </div>


    <div id="product">
        <AboutProduct></AboutProduct>
    </div>

    <div id="workings">
        <Workings></Workings>

    </div>
    <Portfolio></Portfolio>
    <Map />
    <div id="faq">
        <FaqAsk></FaqAsk>

    </div>
    <div id="contact">
        <ContactUs></ContactUs>
    </div>

    <FooterEnd></FooterEnd>
</template>

<style scoped></style>
