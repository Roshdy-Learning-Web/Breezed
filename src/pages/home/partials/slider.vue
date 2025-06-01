<script setup lang="ts">
import { ref, onMounted, onUnmounted } from 'vue';

const images = [
    'images/slide-01.jpg',
    'images/slide-02.jpg',
    'images/slide-03.jpg'
];
const currentIndex = ref(0);
let interval: NodeJS.Timeout | null = null;
const slider = ref<HTMLDivElement | null>(null);

function moveSlider() {
    currentIndex.value = (currentIndex.value + 1) % images.length;
    updateSliderPosition();
}

function updateSliderPosition() {
    if (slider.value) {
        const percentage = -currentIndex.value * 100;
        slider.value.style.transform = `translateX(${percentage}%)`;
    }
}

onMounted(() => {
    interval = setInterval(moveSlider, 5000);
});

onUnmounted(() => {
    if (interval) clearInterval(interval);
});
</script>

<template>
    <div class="hero">
        <div class="hero-images" ref="slider">
            <div class="slide" v-for="(image, index) in images" :key="index">
                <img :src="image" :alt="`background ${index + 1}`" class="hero-img" />
            </div>
        </div>
    </div>
</template>