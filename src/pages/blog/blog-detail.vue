<template>
    <div>
        <navbar />
        <section class="relative pt-32 md:pb-24 pb-16">
            <blogdetail />
        </section>
        <switcher />
        <footers />
    </div>
</template>

<script setup>
import navbar from '@/components/navbar/navbar.vue';
import blogdetail from '@/components/blog/blog-detail.vue';
import switcher from '@/components/switcher.vue';
import footers from '@/components/footer/footer.vue';

</script>

<style lang="scss" scoped></style>