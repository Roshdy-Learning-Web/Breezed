<script setup lang="ts">
import HomeHeader from './partials/header-bar.vue';
import SliderHero from './partials/slider.vue';


</script>

<template>
    <div class="hero">
        <!-- I positioned the header here to be above the images without using z-index -->
        <home-header />
        <slider-hero />

    </div>
</template>