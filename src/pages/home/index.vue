<script setup lang="ts">
import HomeHeader from './partials/header-bar.vue';
import SliderHero from './partials/slider.vue';


</script>

<template>
    <div class="home">
        <slider-hero />
        <!-- I positioned the header here to be above the images without using z-index -->
        <home-header />

    </div>
</template>