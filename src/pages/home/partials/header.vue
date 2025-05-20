<script setup lang="ts">
import { ref, onMounted, onBeforeUnmount } from 'vue'

const isOpen = ref(false)
const isWideScreen = ref(window.innerWidth >= 768)

const handleResize = () => {
    isWideScreen.value = window.innerWidth >= 768
    if (isWideScreen.value) isOpen.value = false
}

onMounted(() => {
    window.addEventListener('resize', handleResize)
})

onBeforeUnmount(() => {
    window.removeEventListener('resize', handleResize)
})
</script>

<template>
    <header>
        <!-- Logo -->
        <h1 class="logo">
            Breezed
        </h1>

        <!-- Navigation -->
        <nav class="menu" :style="{ display: isOpen || isWideScreen ? 'block' : 'none' }">
            <ul class="menu-list">
                <li @click="isOpen = false"><a href="#">Home</a></li>
                <li @click="isOpen = false"><a href="#">About</a></li>
                <li @click="isOpen = false"><a href="#">Services</a></li>
                <li @click="isOpen = false"><a href="#">Contact</a></li>
            </ul>
        </nav>

        <!-- Hamburger Button (visible on small screens) -->
        <button @click="isOpen = !isOpen" class="menu-toggle">
            <svg v-if="!isOpen" width="24" height="24" fill="none" stroke="currentColor" stroke-width="2">
                <path stroke-linecap="round" stroke-linejoin="round" d="M4 6h16M4 12h16M4 18h16" />
            </svg>
            <svg v-else width="24" height="24" fill="none" stroke="currentColor" stroke-width="2">
                <path stroke-linecap="round" stroke-linejoin="round" d="M6 6l12 12M6 18L18 6" />
            </svg>

        </button>
    </header>
</template>

<style scoped>
@media (max-width: 767px) {
    .menu-toggle {
        display: block;
    }

    .menu {
        position: absolute;
        top: 100%;
        width: 90%;
        align-items: center;

    }

    .menu-list {
        padding: 4rem 0;
        flex-direction: column;
        margin-top: 1rem;
        background: #f8f9fa;

        border: 1px solid #dee2e6;
        align-items: center;
        border: 1px solid #c2c2c2;
        border-radius: 5px;
    }

    li {
        width: 70%;
        text-align: center;
        border-bottom: 1px solid #c2c2c296;
        padding-bottom: 1rem;
    }
}
</style>