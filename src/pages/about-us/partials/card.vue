<script setup lang="ts">
const props = defineProps({
    title: {
        type: String,
        default: 'Web Performance'
    },
    description: {
        type: String,
        default: "At its core, the Web operates on a client-server model. Web browsers act as clients that request resources (like HTML, CSS, and JavaScript files) from web servers. These servers respond by sending the requested content, which the browser then renders into a visual web page."
    }
})
</script>

<template>
    <div class="card">
        <img src="/images/features-icon-1.png" alt="">
        <div class="card-body">
            <div>
                <h3>{{ title }}</h3>
                <p>{{ description }}</p>
            </div>

            <a href="#">Learn More &rarr;</a>
        </div>
    </div>
</template>