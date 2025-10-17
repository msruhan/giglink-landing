<template>
    <div>
        <navbar />
        <section class="relative md:pb-24 pb-16 lg:mt-24 mt-[74px]">
            <!-- <creatorprofile /> -->
            <details-workshop :id="id" />
            <div class="container mt-16">
                <!-- <items /> -->
                <!-- <pagination /> -->
            </div><!--end container-->
        </section>
        <switcher />
        <footers />
    </div>
</template>

<script setup>
import { useRoute } from 'vue-router'
import DetailsWorkshop from '@/components/details-workshop.vue'
import navbar from '@/components/navbar/navbar.vue';
// import creatorprofile from '@/components/details-workshop.vue';
// import items from '@/components/discover-items.vue';
// import pagination from '@/components/pagination.vue';
import switcher from '@/components/switcher.vue';
import footers from '@/components/footer/footer.vue'

const route = useRoute()
const id = route.params.id
</script>

<style lang="scss" scoped></style>