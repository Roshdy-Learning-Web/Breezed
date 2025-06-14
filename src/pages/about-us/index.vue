<script lang="ts" setup>
import mainSection from './partials/main-section.vue';
import Card from './partials/card.vue';
</script>
<template>
    <div id="about-us" class="about-us">
        <div class="title">
            <h1>About Us</h1>
        </div>
        <main-section />

        <hr style="border: 1px solid #c2c2c299; width: 80%; margin: 1rem auto;">

        <div class="cards-section">
            <card />
            <card />
            <card />
        </div>
    </div>

</template>