<template>
  <section class="relative py-28 bg-[#f8fafc] overflow-hidden">
    <div class="max-w-7xl mx-auto px-6 lg:px-20 grid md:grid-cols-2 gap-16 items-center">
      <!-- Kiri: Heading -->
      <div>
        <h2
          class="text-5xl md:text-6xl font-extrabold tracking-tight text-gray-900 mb-6 leading-tight font-inter"
        >
          <span class="text-emerald-500">Unleash</span> business’s full potential<span class="text-gray-900">.</span>
        </h2>
      </div>

      <!-- Kanan: Benefit List -->
      <div class="grid sm:grid-cols-1 gap-10">
        <div
          v-for="(item, i) in benefits"
          :key="i"
          class="flex items-start gap-5"
        >
          <!-- Icon -->
          <div
            class="w-14 h-14 rounded-full bg-white shadow-md flex items-center justify-center flex-shrink-0 ring-1 ring-gray-100"
          >
            <i :class="`uil ${item.icon} text-2xl text-emerald-500`"></i>
          </div>
          <!-- Text -->
          <div>
            <h3 class="text-lg font-semibold text-gray-900 font-inter mb-1">
              {{ item.title }}
            </h3>
            <p class="text-gray-500 text-base leading-relaxed font-inter">
              {{ item.desc }}
            </p>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup>
const benefits = [
  {
    icon: "uil-users-alt",
    title: "Tim Ahli SEO",
    desc: "Produk dan strategi kami dirancang untuk meningkatkan visibilitas dan pertumbuhan bisnis Anda.",
  },
  {
    icon: "uil-graph-bar",
    title: "Perencanaan Strategis",
    desc: "Kami bantu menyesuaikan produk Anda dengan kebutuhan pasar dan perilaku pengguna.",
  },
  {
    icon: "uil-headphones-alt",
    title: "Dukungan 24/7",
    desc: "Tim support kami siap membantu kapan pun Anda butuh bantuan — cepat dan responsif.",
  },
];
</script>

<style scoped>
@import url('https://fonts.googleapis.com/css2?family=Inter:wght@400;500;600;700;800&display=swap');

.font-inter {
  font-family: 'Inter', sans-serif;
}

.shadow-md {
  box-shadow: 0 6px 18px rgba(0, 0, 0, 0.05);
}

.ring-gray-100 {
  --tw-ring-color: rgba(0, 0, 0, 0.05);
}
</style>
