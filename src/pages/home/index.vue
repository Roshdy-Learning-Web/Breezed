<script setup lang="ts">
import { ref, onMounted,onUnmounted } from 'vue';
import HomeHeader from './partials/header.vue';

const images = [
    'images/slide-01.jpg',
    'images/slide-02.jpg',
    'images/slide-03.jpg'
];
const currentIndex = ref(1);
var interval: NodeJS.Timeout | null = null;
onMounted(() => {
    interval = setInterval(() => {
        currentIndex.value = (currentIndex.value + 1) % images.length;
    }, 5000);

})

onUnmounted(() => {
    clearInterval(interval);
});

</script>

<template>
    <div class="hero">
        <div class="hero-images" v-for="(image, index) in images" :key="image">
            <img  :src=" image" :alt="`background ${index + 1}`" :class="['hero-img',{'active': index === currentIndex}]" />
        </div>

        <!-- I positioned the header here to be above the images without using z-index -->
        <home-header />
    </div>
</template>