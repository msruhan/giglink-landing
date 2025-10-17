<template>
    <div class="container">
        <div class="grid lg:grid-cols-3 md:grid-cols-2 grid-cols-1 gap-[30px]">
            <div v-for="item in datas" :key="item" class="">
                <h5 class="font-semibold text-xl">{{ item.title }}</h5>
                <ul class="list-none mt-4">
                    <li v-for="list in item.list" :key="list" class="mt-2"><a href="" class="text-slate-400"><i class="mdi mdi-arrow-right text-violet-600 me-2"></i>{{ list }}</a></li>
                </ul>
            </div>
        </div><!--end grid-->
    </div><!--end container-->
</template>

<script setup>

const datas = [
    {
        title: 'Getting started',
        list: ['Deciding to purchase', 'List your space', 'Landing an experience or adventure', 'Top uses questions']
    },
    {
        title: 'Your calendar',
        list: ['Pricing & availability', 'Booking settings', 'Responding to enquiries & requests', 'Snoozing or deactivating your listing']
    },
    {
        title: 'Your listings',
        list: ['Updating your listing', 'Neighbourhoods', 'Listing photos & photography', 'Giglink Plus', 'API-connected software']
    },
    {
        title: 'How payouts work',
        list: ['Getting paid', 'Adding payout info', 'Your payout status', 'Donations', 'Taxes']
    },
    {
        title: 'Your reservations',
        list: ['Giglink safely', 'Giglink Experiences and Adventures', 'Changing a reservation', 'Cancelling a reservation', 'Long-term reservations']
    },
    {
        title: 'Reservation help',
        list: ['Help with a reservation or guest', 'Guest cancellations']
    },
    {
        title: 'Your account',
        list: ['Your profile', 'Account security', 'Identification & verifications', 'Reviews', 'Superhost status']
    },
]
</script>

<style lang="scss" scoped></style>