<template>
  <div class="flex flex-col min-h-screen">
    <header class="bg-white shadow-md">
      <div class="container mx-auto px-4 py-4 flex justify-between items-center">
        <router-link to="/" class="text-2xl font-bold text-purple-700">ShopAnalyzer</router-link>
        <nav>
          <ul class="flex space-x-4">
            <li><router-link to="/shops" class="text-gray-600 hover:text-purple-700">Shops</router-link></li>
            <li><router-link to="/analysis" class="text-gray-600 hover:text-purple-700">Analysis</router-link></li>
            <li><router-link to="/notifications" class="text-gray-600 hover:text-purple-700">Notifications</router-link></li>
            <li>
              <button class="px-4 py-2 border border-purple-700 text-purple-700 rounded hover:bg-purple-700 hover:text-white transition-colors">
                Login
              </button>
            </li>
          </ul>
        </nav>
      </div>
    </header>

    <main class="flex-grow">
      <!-- Hero Section -->
      <section class="bg-gradient-to-r from-purple-700 to-indigo-800 text-white py-20">
        <div class="container mx-auto px-4">
          <h1 class="text-4xl md:text-6xl font-bold mb-4">Track Shop Performance with Ease</h1>
          <p class="text-xl mb-8">Analyze shops, track performance, and receive automated notifications.</p>
          <button class="bg-white text-purple-700 px-6 py-3 rounded-full font-semibold hover:bg-gray-100 transition-colors">
            Get Started
          </button>
        </div>
      </section>

      <!-- Top Performing Shops Section -->
      <section class="py-16 bg-gray-100">
        <div class="container mx-auto px-4">
          <h2 class="text-3xl font-bold mb-8 text-center">Top Performing Shops</h2>
          <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-8">
            <div v-for="shop in topShops" :key="shop.id" class="bg-white rounded-lg shadow-md overflow-hidden">
              <div class="p-6">
                <h3 class="text-xl font-semibold mb-2">{{ shop.name }}</h3>
                <p class="mb-4">Performance Score: {{ shop.score }}</p>
                <ShopPerformanceChart :data="shop.performanceData" />
              </div>
            </div>
          </div>
        </div>
      </section>

      <!-- Notification System Section -->
      <section class="py-16">
        <div class="container mx-auto px-4">
          <h2 class="text-3xl font-bold mb-8 text-center">Stay Informed with Our Notification System</h2>
          <div class="grid grid-cols-1 md:grid-cols-2 gap-8 items-center">
            <div>
              <h3 class="text-2xl font-semibold mb-4">How It Works</h3>
              <ul class="list-disc list-inside space-y-2">
                <li>Subscribe to shops you want to track</li>
                <li>Receive daily or weekly email reports</li>
                <li>Get instant alerts for significant changes</li>
                <li>Customize your notification preferences</li>
              </ul>
            </div>
            <div class="bg-gray-200 p-8 rounded-lg">
              <h3 class="text-2xl font-semibold mb-4">Subscribe Now</h3>
              <p class="mb-4">Start receiving shop performance reports today!</p>
              <button class="bg-purple-700 text-white px-6 py-3 rounded-full font-semibold hover:bg-purple-800 transition-colors">
                Subscribe to Notifications
              </button>
            </div>
          </div>
        </div>
      </section>
    </main>

    <footer class="bg-gray-800 text-white py-8">
      <div class="container mx-auto px-4 text-center">
        <p>&copy; {{ currentYear }} Shop Analysis Platform. All rights reserved.</p>
      </div>
    </footer>
  </div>
</template>

<script setup>
import { ref } from 'vue';
import { Line } from 'vue-chartjs';
import { Chart as ChartJS, CategoryScale, LinearScale, PointElement, LineElement, Title, Tooltip, Legend } from 'chart.js';

ChartJS.register(CategoryScale, LinearScale, PointElement, LineElement, Title, Tooltip, Legend);

const currentYear = new Date().getFullYear();

const topShops = ref([
  { id: 1, name: "Electro World", score: 95, performanceData: [65, 70, 80, 85, 90, 95] },
  { id: 2, name: "Fashion Haven", score: 92, performanceData: [70, 75, 78, 80, 88, 92] },
  { id: 3, name: "Gourmet Delights", score: 88, performanceData: [60, 68, 72, 80, 85, 88] },
]);

const ShopPerformanceChart = {
  extends: Line,
  props: ['data'],
  mounted() {
    this.renderChart({
      labels: ['Jan', 'Feb', 'Mar', 'Apr', 'May', 'Jun'],
      datasets: [
        {
          label: 'Performance Score',
          data: this.data,
          borderColor: 'rgb(75, 192, 192)',
          tension: 0.1,
        },
      ],
    }, {
      responsive: true,
      maintainAspectRatio: false,
      plugins: {
        legend: {
          display: false,
        },
      },
      scales: {
        y: {
          beginAtZero: true,
          max: 100,
        },
      },
    });
  },
};
</script>