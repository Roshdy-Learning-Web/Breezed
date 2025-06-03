<script setup lang="ts">
import { ref, onMounted, onUnmounted } from 'vue';

const images = [
    {
        image:'images/slide-01.jpg',
        title: 'Welcome to Breezed',
        subtitle: 'Discover a world of endless possibilities',
    },
    {
        image:'images/slide-02.jpg',
        title: 'High performance',
        subtitle: 'largest contentful paint optimization for faster loading',
    },
    {
        image:'images/slide-03.jpg',
        title: 'accessibility background',
        subtitle: 'Design for everyone with accessibility in mind',
    }
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
            <div class="slide" v-for="(item, index) in images" :key="index">
                    <img :src="item.image" :alt="`background ${index + 1}`" class="hero-img" />
                    <div class="hero-overlay">
                        <div class="hero-content">
                            <h1 class="hero-title">{{ item.title }}</h1>
                            <p class="hero-subtitle">{{ item.subtitle }}</p>
                        </div>
                        <div class="gap-2">
                            <button class="hero-button btn1">Learn More</button>
                            <button class="hero-button btn-2">Get Started</button>
                        </div>
                    </div>
            </div>
        </div>

    </div>
</template>