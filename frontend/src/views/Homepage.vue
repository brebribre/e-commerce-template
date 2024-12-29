<template>
  <div class="min-h-screen bg-yellow-50 font-poppins">
    <!-- Header -->
    <header class="sticky top-0 z-50 w-full border-b bg-yellow-400 text-gray-900">
      <div class="container mx-auto px-4 sm:px-6 lg:px-8">
        <div class="flex h-16 items-center justify-between">
          <!-- Logo -->
          <div class="flex-shrink-0 mr-8">
            <a href="#" class="text-2xl font-bold">FitGear</a>
          </div>

          <!-- Navigation -->
          <nav class="hidden md:flex space-x-10">
            <a v-for="item in navItems" :key="item"  class="text-gray-900 hover:text-yellow-700">
              {{ item }}
            </a>
          </nav>

          <!-- Search Bar -->
          <div class="flex-1 flex justify-center px-2 lg:ml-6 lg:justify-end">
            <div class="max-w-lg w-full lg:max-w-xs">
              <label for="search" class="sr-only">Search</label>
              <div class="relative">
                <div class="absolute inset-y-0 left-0 pl-3 flex items-center pointer-events-none">
                  <SearchIcon class="h-5 w-5 text-gray-600" />
                </div>
                <input id="search" name="search" class="block w-full pl-10 pr-3 py-2 border border-yellow-300 rounded-md leading-5 bg-yellow-100 placeholder-gray-500 focus:outline-none focus:placeholder-gray-400 focus:ring-1 focus:ring-yellow-500 focus:border-yellow-500 sm:text-sm" placeholder="Search products" type="search">
              </div>
            </div>
          </div>

          <!-- User Icons -->
          <div class="flex items-center">
            <button class="p-1 rounded-full text-gray-700 hover:text-gray-900 focus:outline-none focus:ring-2 focus:ring-offset-2 focus:ring-yellow-500">
              <span class="sr-only">View account</span>
              <UserIcon class="h-6 w-6" />
            </button>
            <button class="ml-3 p-1 rounded-full text-gray-700 hover:text-gray-900 focus:outline-none focus:ring-2 focus:ring-offset-2 focus:ring-yellow-500">
              <span class="sr-only">View cart</span>
              <ShoppingCartIcon class="h-6 w-6" />
            </button>
          </div>
        </div>
      </div>
    </header>

    <!-- Hero Section -->
    <section class="bg-gradient-to-r from-yellow-400 to-yellow-300 text-gray-900">
      <div class="container mx-auto px-4 py-24 sm:px-6 lg:px-8 flex flex-col items-center">
        <h1 class="text-4xl font-extrabold tracking-tight sm:text-5xl md:text-6xl text-center">
          Elevate Your Fitness Journey
        </h1>
        <p class="mt-6 max-w-2xl text-xl text-center text-gray-800">
          Discover top-quality fitness gear to help you reach your goals. Get fit, stay strong, and push your limits!
        </p>
        <div class="mt-10 flex justify-center">
          <button class="bg-gray-900 text-yellow-400 hover:bg-gray-800 px-6 py-3 rounded-md text-lg font-medium">
            Shop Now
          </button>
          <button class="ml-4 bg-yellow-500 text-gray-900 hover:bg-yellow-400 px-6 py-3 rounded-md text-lg font-medium">
            View Workouts
          </button>
        </div>
      </div>
    </section>

    <!-- Product Categories -->
    <section class="py-16">
      <div class="container mx-auto px-4 sm:px-6 lg:px-8">
        <h2 class="text-3xl font-extrabold tracking-tight text-gray-900 sm:text-4xl mb-8">
          Shop by Category
        </h2>
        <div class="grid gap-6 grid-cols-1 sm:grid-cols-2 md:grid-cols-3 lg:grid-cols-4">
          <div v-for="category in categories" :key="category.name" class="group">
            <div class="aspect-w-1 aspect-h-1 bg-yellow-200 rounded-lg overflow-hidden">
              <img :src="category.image" :alt="category.name" class="w-full h-full object-center object-cover group-hover:opacity-75 transition duration-300 ease-in-out transform group-hover:scale-105">
            </div>
            <div class="mt-4 flex justify-between items-center">
              <h3 class="text-sm font-medium text-gray-900">
                <a href="#" class="hover:text-yellow-600 transition duration-300 ease-in-out">
                  <span class="absolute inset-0"></span>
                  {{ category.name }}
                </a>
              </h3>
              <p class="text-sm font-semibold text-gray-900">{{ formatPrice(category.price) }}</p>
            </div>
            <p class="mt-1 text-sm text-yellow-600">Explore Now</p>
          </div>
        </div>
      </div>
    </section>
  </div>
</template>

<script setup>
import { ref } from 'vue'
import { SearchIcon, UserIcon, ShoppingCartIcon } from 'lucide-vue-next'

const navItems = ref(['Home', 'Shop', 'Workouts', 'About', 'Contact'])

const categories = ref([
  { name: 'Cardio Equipment', image: 'https://placehold.co/600x400', price: 15000000 },
  { name: 'Strength Training', image: 'https://placehold.co/600x400', price: 8000000 },
  { name: 'Yoga & Pilates', image: 'https://placehold.co/600x400', price: 2000000 },
  { name: 'Fitness Apparel', image: 'https://placehold.co/600x400', price: 500000 },
  { name: 'Cardio Equipment', image: 'https://placehold.co/600x400', price: 15000000 },
  { name: 'Strength Training', image: 'https://placehold.co/600x400', price: 8000000 },
  { name: 'Yoga & Pilates', image: 'https://placehold.co/600x400', price: 2000000 },
  { name: 'Fitness Apparel', image: 'https://placehold.co/600x400', price: 500000 },
])

const formatPrice = (price) => {
  return new Intl.NumberFormat('id-ID', { style: 'currency', currency: 'IDR' }).format(price)
}
</script>

<style>
@import url('https://fonts.googleapis.com/css2?family=Poppins:wght@300;400;500;600;700&display=swap');

.font-poppins {
  font-family: 'Poppins', sans-serif;
}
</style>

