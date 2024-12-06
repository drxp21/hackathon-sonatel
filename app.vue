<template>
  <div class="relative min-h-screen bg-white">
    <!-- Navbar -->
    <header class="bg-white">
      <nav class="container mx-auto px-4 flex justify-between items-center h-16">
        <!-- Brand Logo -->
        <router-link to="/" class="text-lg font-semibold text-gray-700">
          Compagnon du pélerin
        </router-link>

        <!-- Desktop Menu -->
        <ul class="hidden md:flex space-x-6">
          <li>
            <NuxtLink v-for="link in navLinks" :to="link.url" class="text-gray-600 hover:text-blue-500 ml-5">{{ link.name
            }}
            </NuxtLink>
          </li>
        </ul>

        <!-- Mobile Menu Button -->
        <button class="md:hidden text-gray-600" @click="toggleMenu">
          <svg xmlns="http://www.w3.org/2000/svg" :class="isMenuOpen ? 'hidden' : 'block'" class="h-6 w-6" fill="none"
            viewBox="0 0 24 24" stroke="currentColor" stroke-width="2">
            <path stroke-linecap="round" stroke-linejoin="round" d="M4 6h16M4 12h16M4 18h16" />
          </svg>
          <svg xmlns="http://www.w3.org/2000/svg" :class="isMenuOpen ? 'block' : 'hidden'" class="h-6 w-6" fill="none"
            viewBox="0 0 24 24" stroke="currentColor" stroke-width="2">
            <path stroke-linecap="round" stroke-linejoin="round" d="M6 18L18 6M6 6l12 12" />
          </svg>
        </button>
      </nav>

      <!-- Mobile Dropdown -->
      <ul :class="isMenuOpen ? 'max-h-screen' : 'max-h-0'"
        class="transition-all duration-300 overflow-hidden md:hidden bg-gray-50 border-t border-gray-200">
        <li>
          <NuxtLink @click="isMenuOpen = !isMenuOpen" v-for="link in navLinks" :to="link.url"
            class="block px-4 py-2 text-gray-600 hover:text-blue-500">{{
              link.name }}
          </NuxtLink>
        </li>

      </ul>
    </header>

    <!-- Page Content -->
    <transition name="fade" mode="out-in">
      <NuxtPage />
    </transition>
  </div>
  <div>
    <!-- Darkened Overlay -->
    <div
      v-if="showChatBubble"
      class="fixed inset-0 bg-black bg-opacity-50 transition-opacity duration-300"
      @click="toggleChatBubble"
    ></div>

    <!-- Floating Action Button -->
    <div
      class="fixed bottom-5 right-5 w-16 h-16 bg-blue-500 text-white text-2xl flex items-center justify-center rounded-full shadow-lg cursor-pointer"
      @click="toggleChatBubble"
    >
      💬
    </div>

    <!-- Chat Bubble -->
    <div
      v-if="showChatBubble"
      class="fixed bottom-0 sm:inset-0 sm:m-auto sm:w-full sm:h-full lg:right-5 lg:w-1/4 lg:h-auto lg:rounded-lg bg-white shadow-lg transition-transform duration-300 transform scale-95 sm:scale-100"
    >
      <div class="bg-blue-500 text-white flex justify-between items-center p-4 rounded-t-lg lg:rounded-t-none">
        <h3 class="text-lg font-semibold">Chatbot en Wolof</h3>
        <button
          class="text-white text-xl focus:outline-none"
          @click="toggleChatBubble"
        >
          ×
        </button>
      </div>
      <div class="p-4 overflow-y-auto max-h-96">
        <p><strong>Bot:</strong> Salaamaalekum! Naka nga def?</p>
        <p><strong>User:</strong> Maangi fi rek, yaangi noos?</p>
        <p><strong>Bot:</strong> Waaw, dama noos. Naka laa may ci ndimbal?</p>
      </div>
    </div>
  </div>
</template>

<script setup>
import { ref } from 'vue';

const isMenuOpen = ref(false);
const showChatBubble = ref(false);

const navLinks = [
  {
    name: 'Accueil',
    url: '/'
  },
  {
    name: 'Pèlerinages',
    url: '/pilgrimages'
  },
  {
    name: "Pain de vie numérique",
    url: '/panem'
  }
]
function toggleMenu() {
  isMenuOpen.value = !isMenuOpen.value;
}
</script>

<style scoped>
/* Add a smooth fade effect for router-view */
.fade-enter-active,
.fade-leave-active {
  transition: opacity 0.3s ease;
}

.fade-enter-from,
.fade-leave-to {
  opacity: 0;
}

.chat-bubble {
  position: fixed;
  bottom: 90px;
  right: 20px;
  width: 300px;
  max-width: 90%;
  background-color: white;
  border: 1px solid #ddd;
  border-radius: 10px;
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
  display: flex;
  flex-direction: column;
}

/* Chat Header */
.chat-header {
  background-color: #007bff;
  color: white;
  padding: 10px;
  font-size: 16px;
  display: flex;
  justify-content: space-between;
  align-items: center;
}

/* Close Button */
.close-btn {
  background: none;
  border: none;
  color: white;
  font-size: 18px;
  cursor: pointer;
}

/* Chat Content */
.chat-content {
  padding: 10px;
  font-size: 14px;
  color: #333;
  max-height: 200px;
  overflow-y: auto;
}

.chat-content p {
  margin: 0 0 10px;
}
</style>