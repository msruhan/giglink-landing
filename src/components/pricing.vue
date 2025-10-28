<template>
  <section class="relative bg-[#f9f9f9] dark:bg-[#0f0f0f] py-24 overflow-hidden">
    <div class="container mx-auto px-6 lg:px-20 text-center">
      <!-- Header -->
      <div class="mb-16">
        <span class="inline-flex items-center justify-center text-xs font-semibold text-gray-700 bg-white shadow-sm px-4 py-1 rounded-full mb-4">
          ⭐ BENEFITS
        </span>
        <h2 class="text-5xl md:text-6xl font-bold text-black dark:text-white mb-4">
          Why Choose Us
        </h2>
        <p class="text-gray-500">
          Partner with an AI agency delivering smart solutions.
        </p>
      </div>

      <!-- Cards -->
      <div class="grid md:grid-cols-3 gap-8 mb-12 max-w-6xl mx-auto">
        <!-- Card 1 -->
        <div class="relative bg-white/60 dark:bg-white/10 backdrop-blur-xl rounded-2xl shadow-[inset_2px_2px_8px_rgba(255,255,255,0.6),inset_-2px_-2px_8px_rgba(0,0,0,0.05)] border border-white/30 p-10 text-left hover:shadow-lg transition">
          <div class="flex flex-col items-center mb-6">
            <div class="w-24 h-24 rounded-full bg-white shadow-inner flex items-center justify-center mb-6">
              <div class="w-8 h-1.5 bg-black rounded-full rotate-45"></div>
            </div>
            <h3 class="text-lg font-semibold text-black dark:text-white">Real-Time Analytics</h3>
            <p class="text-gray-500 text-sm mt-2 text-center">
              Stay ahead with accurate, real-time performance tracking.
            </p>
          </div>
        </div>

        <!-- Card 2 -->
        <div class="relative bg-white/60 dark:bg-white/10 backdrop-blur-xl rounded-2xl shadow-[inset_2px_2px_8px_rgba(255,255,255,0.6),inset_-2px_-2px_8px_rgba(0,0,0,0.05)] border border-white/30 p-10 text-left hover:shadow-lg transition">
          <div class="flex flex-col items-center mb-6 relative">
            <div class="absolute top-6 left-6 text-xs bg-white/70 px-3 py-1 rounded-full shadow-sm text-gray-700 font-medium">20% Automation</div>
            <div class="absolute top-6 right-6 text-xs bg-white/70 px-3 py-1 rounded-full shadow-sm text-gray-700 font-medium">60% Cost</div>
            <div class="w-24 h-24 rounded-full bg-white shadow-inner flex items-center justify-center mb-6">
              <div class="w-10 h-10 bg-gradient-to-t from-gray-200 to-white rounded-md"></div>
            </div>
            <h3 class="text-lg font-semibold text-black dark:text-white">AI-Driven Growth</h3>
            <p class="text-gray-500 text-sm mt-2 text-center">
              Make smarter moves with accurate, real-time business insights.
            </p>
          </div>
        </div>

        <!-- Card 3 -->
        <div class="relative bg-white/60 dark:bg-white/10 backdrop-blur-xl rounded-2xl shadow-[inset_2px_2px_8px_rgba(255,255,255,0.6),inset_-2px_-2px_8px_rgba(0,0,0,0.05)] border border-white/30 p-10 text-left hover:shadow-lg transition">
          <div class="flex flex-col items-center mb-6">
            <div class="w-24 h-24 rounded-full bg-white shadow-inner flex items-center justify-center mb-6 relative">
              <div class="absolute top-3 left-3 w-10 h-10 bg-black rounded-md"></div>
            </div>
            <h3 class="text-lg font-semibold text-black dark:text-white">Sync in real time</h3>
            <p class="text-gray-500 text-sm mt-2 text-center">
              Connect with your team instantly to track progress and updates.
            </p>
          </div>
        </div>
      </div>

      <!-- Feature tags -->
      <div class="flex flex-wrap justify-center gap-4">
        <span class="px-5 py-2 bg-white shadow-sm rounded-full text-sm text-gray-400 flex items-center gap-2">
          <i class="uil uil-layer-group"></i> Scalable Solutions
        </span>
        <span class="px-5 py-2 bg-white shadow-sm rounded-full text-sm text-gray-700 flex items-center gap-2">
          ⚙️ Personalized Experiences
        </span>
        <span class="px-5 py-2 bg-white shadow-sm rounded-full text-sm text-gray-700 flex items-center gap-2">
          💰 Cost Effective
        </span>
        <span class="px-5 py-2 bg-white shadow-sm rounded-full text-sm text-gray-700 flex items-center gap-2">
          📊 Real-Time Insights
        </span>
        <span class="px-5 py-2 bg-white shadow-sm rounded-full text-sm text-gray-700 flex items-center gap-2">
          🤖 Automation
        </span>
      </div>
    </div>
  </section>
</template>

<script setup>
// purely static visual component
</script>
