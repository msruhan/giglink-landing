<template>
  <section class="py-28 bg-white">
    <div class="max-w-7xl mx-auto px-6 lg:px-20">
      <!-- Judul -->
      <div class="text-center mb-16">
        <h2
          class="text-4xl md:text-5xl font-extrabold text-gray-900 mb-4 font-inter leading-tight"
        >
          Empower your business <br />
          with cutting-edge <span class="text-emerald-500">solutions.</span>
        </h2>
      </div>

      <!-- Step List -->
      <div
        class="grid sm:grid-cols-3 gap-10 border-b border-gray-200 pb-10 mb-16 text-center sm:text-left"
      >
        <div
          v-for="(step, index) in steps"
          :key="index"
          @click="activeStep = index"
          class="flex flex-col sm:flex-row sm:items-start gap-4 sm:gap-6 cursor-pointer transition"
        >
          <h3
            class="text-4xl font-bold leading-none font-inter sm:w-16"
            :class="activeStep === index ? 'text-emerald-500' : 'text-gray-300'"
          >
            {{ step.number }}
          </h3>
          <div>
            <p
              class="text-lg font-semibold font-inter"
              :class="activeStep === index ? 'text-gray-900' : 'text-gray-500'"
            >
              {{ step.title }}
            </p>
            <p class="text-gray-500 text-sm leading-relaxed font-inter">
              {{ step.desc }}
            </p>
          </div>
        </div>
      </div>

      <!-- Gambar & Konten Dinamis -->
      <transition name="fade" mode="out-in">
        <div
          :key="activeStep"
          class="grid md:grid-cols-2 gap-16 items-center"
        >
          <!-- Gambar -->
          <div>
            <img
              :src="steps[activeStep].image"
              :alt="steps[activeStep].title"
              class="rounded-2xl shadow-md"
            />
          </div>

          <!-- Konten -->
          <div>
            <h3 class="text-2xl font-bold text-gray-900 mb-4 font-inter">
              {{ steps[activeStep].title }}
            </h3>
            <p class="text-gray-600 mb-6 leading-relaxed font-inter">
              {{ steps[activeStep].content }}
            </p>

            <ul class="space-y-3 mb-8">
              <li
                v-for="(item, i) in steps[activeStep].features"
                :key="i"
                class="flex items-start gap-3 text-gray-700"
              >
                <i
                  class="uil uil-check-circle text-emerald-500 text-xl mt-0.5"
                ></i>
                <span class="font-inter leading-relaxed">{{ item }}</span>
              </li>
            </ul>

            <button
              class="bg-emerald-500 text-white px-6 py-3 rounded-lg font-semibold text-sm shadow-md hover:bg-emerald-600 transition"
            >
              Request A Free Demo
            </button>
          </div>
        </div>
      </transition>
    </div>
  </section>
</template>

<script setup>
import { ref } from "vue";

const activeStep = ref(0);

const steps = [
  {
    number: "01",
    title: "Collect Ideas",
    desc: "Gathering creative inspiration for your next project.",
    content:
      "We help you collect and organize the most valuable ideas from your team and customers, turning creativity into actionable insights.",
    features: [
      "Brainstorm with diverse teams for fresh perspectives.",
      "Use structured frameworks for idea evaluation.",
      "Prioritize high-impact concepts quickly.",
    ],
    image:
      "https://images.unsplash.com/photo-1587614382346-4ec70e388b28?auto=format&fit=crop&w=900&q=80",
  },
  {
    number: "02",
    title: "Data Analysis",
    desc: "Transform data into strategic business intelligence.",
    content:
      "Our data analysis tools provide deep insights, helping you make informed decisions with confidence and accuracy.",
    features: [
      "Visualize your key performance indicators easily.",
      "Automate repetitive analysis workflows.",
      "Gain real-time insights to optimize performance.",
    ],
    image:
      "https://images.unsplash.com/photo-1556157382-97eda2d62296?auto=format&fit=crop&w=900&q=80",
  },
  {
    number: "03",
    title: "Finalize Product",
    desc: "Deliver excellence with seamless execution.",
    content:
      "After ideation and analysis, we help you bring your product vision to life with efficient workflows and top-tier quality assurance.",
    features: [
      "Collaborate across teams effortlessly.",
      "Streamline your launch process.",
      "Deliver consistent, reliable results to your customers.",
    ],
    image:
          "https://images.unsplash.com/photo-1587614382346-4ec70e388b28?auto=format&fit=crop&w=900&q=80",
  },
];
</script>

<style scoped>
@import url("https://fonts.googleapis.com/css2?family=Inter:wght@400;500;600;700;800&display=swap");
.font-inter {
  font-family: "Inter", sans-serif;
}

.fade-enter-active,
.fade-leave-active {
  transition: all 0.4s ease;
}
.fade-enter-from {
  opacity: 0;
  transform: translateY(20px);
}
.fade-leave-to {
  opacity: 0;
  transform: translateY(-20px);
}
</style>
