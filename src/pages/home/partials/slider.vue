<script setup lang="ts">
import { ref, onMounted, onUnmounted } from 'vue';

const images = [
    {
        image: 'images/slide-01.jpg',
        title: 'Welcome to Breezed',
        subtitle: 'Discover a world of endless possibilities',
    },
    {
        image: 'images/slide-02.jpg',
        title: 'High performance',
        subtitle: 'largest contentful paint optimization for faster loading',
    },
    {
        image: 'images/slide-03.jpg',
        title: 'accessibility background',
        subtitle: 'Design for everyone with accessibility in mind',
    }
];
const currentIndex = ref(0);
let interval: NodeJS.Timeout | null = null;
const slider = ref<HTMLDivElement | null>(null);
const isMovingLeft = ref(false);

function moveSliderRight() {
    clearInterval(interval);
    currentIndex.value = (currentIndex.value + 1) % images.length;
    isMovingLeft.value = false;
    updateSliderPosition();
}

function moveSliderLeft() {
    clearInterval(interval);
    currentIndex.value = (currentIndex.value - 1 + images.length) % images.length;
    updateSliderPosition();
}

function moveSlider() {
    if (currentIndex.value === 0) {
        isMovingLeft.value = false;
        moveSliderRight();
        return
    }
    if (currentIndex.value === images.length - 1 || isMovingLeft.value) {
        isMovingLeft.value = true;
        moveSliderLeft();
        return
    }
    moveSliderRight();

}

function updateSliderPosition() {
    if (slider.value) {
        const percentage = -currentIndex.value * 100;
        slider.value.style.transform = `translateX(${percentage}%)`;
        interval = setInterval(moveSlider, 5000);
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
        <div class="arrows">
            <img src="/public/images/next.png" alt="next icon " class="next icon" @click="moveSliderRight" />
            <img src="/public/images/prev.png" alt="previous icon" class="icon prev" @click="moveSliderLeft" />
        </div>
    </div>
</template>