<script setup>
// import { RouterLink, RouterView } from 'vue-router'
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
import OurCustomers from './components/OurCustomers.vue'
import Banner2 from './components/Banner2.vue'
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
    <Banner2></Banner2>
    <OurCustomers></OurCustomers>
    <div id="faq">
        <FaqAsk></FaqAsk>
    </div>
    <Map />
    <div id="contact">
        <ContactUs></ContactUs>
    </div>

    <FooterEnd></FooterEnd>
</template>

<style scoped></style>
