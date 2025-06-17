<script lang="ts" setup>
import mainSection from './partials/main-section.vue';
import Card from './partials/card.vue';
const cardsInformation = [
    {
        title: 'Web Performance',
        description: 'At its core, the Web operates on a client-server model. Web browsers act as clients that request resources (like HTML, CSS, and JavaScript files) from web servers. These servers respond by sending the requested content, which the browser then renders into a visual web page.',
    },
    {
        title: 'Responsive Design',
        description: 'Responsive design ensures websites look and function well on all devices by using flexible layouts, fluid grids, and media queries.',
    },
    {
        title: 'SEO Fundamentals',
        description: 'Search Engine Optimization improves the visibility of a website on search engines. Important factors include page speed, metadata, mobile-friendliness, and clean URLs.',
    },
    // {
    //     title: 'Accessibility (a11y)',
    //     description: 'Accessibility means building websites usable by everyone, including people with disabilities. This includes using semantic HTML, ARIA roles, and proper contrast ratios.',
    // },
    // {
    //     title: 'Caching Strategies',
    //     description: 'Caching improves performance by storing frequently accessed data closer to the user. Techniques like browser caching, service workers, and CDN edge caching can drastically reduce load times.',
    // },
    // {
    //     title: 'Single Page Applications (SPA)',
    //     description: 'SPAs load a single HTML page and dynamically update content without refreshing the page. They offer smooth user experiences but require careful routing and state management.',
    // },
    // {
    //     title: 'Progressive Web Apps (PWA)',
    //     description: 'PWAs offer app-like experiences using modern APIs like service workers, offline support, and home screen installation.',
    // },
    // {
    //     title: 'Security Best Practices',
    //     description: 'Secure web development involves HTTPS, input validation, content security policies, and preventing attacks like XSS and CSRF.',
    // }
]
</script>
<template>
    <div id="about-us" class="about-us">
        <div class="title">
            <h1>About Us</h1>
        </div>
        <main-section />

        <hr style="border: 1px solid #c2c2c299; width: 80%; margin: 1rem auto;">

        <div class="cards-section">
            <card  v-for="card in cardsInformation" :key="card.title" :title="card.title" :description="card.description"/>
           
        </div>
    </div>

</template>