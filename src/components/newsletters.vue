<script setup>
</script>

<template>
    <div class="newsletter">
        <div class="newsletter-title">
            <h3>Subscribe to our newsletter</h3>
            <h4>Don’t miss this chance!</h4>
            <p>
                Stay updated with the latest news and offers from our team. Sign up for our newsletter to stay up to date
                with our latest products.
            </p>
        </div>
        <form class="newsletter-input" @submit.prevent>
            <input type="email" placeholder="Email Address">
            <button type="submit">Subscribe</button>
        </form>
    </div>
</template>