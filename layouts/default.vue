<template>
<div class="flex flex-col min-h-screen"> <!-- Flex container with minimum height of the viewport -->
  <nav class="flex items-center justify-between flex-wrap bg-transparent p-6 lg:px-24">
    <div :class="{'whitelogo': isOpen, 'z-10': true}" class="flex items-center flex-shrink-0 text-white">
      <NuxtLink to="/">
        <Logo />
      </NuxtLink>
    </div>
    <div class="text-sm flex-grow flex items-center justify-end lg:flex">
      <div class="hidden lg:flex">
        <NuxtLink
          to="/"
          class="inline-block flex items-center mr-9 text-base font-sans font-semibold text-black hover:text-blue-900"
        >
          Home
        </NuxtLink>
        <NuxtLink
          to="/"
          class="inline-block flex items-center mr-9 text-base font-sans font-semibold text-black hover:text-blue-900"
        >
          About
        </NuxtLink>
        <NuxtLink to="/" class="inline-block flex items-center">
          <button class="px-6 py-1.5 text-base font-sans font-semibold text-white bg-emerald-400 hover:bg-emerald-300 rounded-md">
            Contact
          </button>
        </NuxtLink>
      </div>
      <div class="lg:hidden">
        <button @click="toggleNavbar" :class="{'hamburger': true, 'active': isOpen}">
          <span></span>
          <span></span>
          <span></span>
        </button>
      </div>
    </div>
    <div v-if="isOpen" class="lg:hidden">
      <div class="overlay" @click="toggleNavbar">
        <div class="offcanvas">
          <div class="flex flex-col items-center">
            <NuxtLink to="/" class="block w-full text-center py-2 mt-2 text-3xl font-sans font-semibold text-white">
              Home
            </NuxtLink>
            <NuxtLink to="/" class="block w-full text-center py-2 mt-2 text-3xl font-sans font-semibold text-white">
              About
            </NuxtLink>
            <NuxtLink to="/" class="block w-full text-center py-2 mt-2 text-3xl font-sans font-semibold text-white">
              Contact
            </NuxtLink>
          </div>
        </div>
      </div>
    </div>
  </nav>
  <main>
  <nuxt/>
  </main>
  <footer class="bg-white text-black text-center p-4">
    © {{ new Date().getFullYear() }} Name
  </footer>
</div>
</template>
<script>
import Logo from '~/components/logo.vue'; // Import the Logo component

export default {
  components: {
    Logo // Register the Logo component
  },
  data() {
    return {
      isOpen: false
    };
  },
  methods: {
    toggleNavbar() {
      this.isOpen = !this.isOpen;
    }
  }
};
</script>
<style>
.hamburger {
    width: 30px;
    height: 20px;
    display: flex;
    flex-direction: column;
    justify-content: space-between;
    cursor: pointer;
}

.hamburger span {
    display: block;
    width: 30px;
    height: 3px;
    background-color: black;
    border-radius: 3px;
    transition: all 0.3s ease;
    z-index: 1;
}
  
.hamburger.active span:nth-child(1) {
    transform: translateY(9px) rotate(45deg);
    background-color: white;
}
  
.hamburger.active span:nth-child(2) {
    opacity: 0;
}
  
.hamburger.active span:nth-child(3) {
    transform: translateY(-9px) rotate(-45deg);
    background-color: white;
}

.overlay {
    position: fixed;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    background-color: rgba(0, 0, 0, 1);
    display: flex;
    align-items: center;
    justify-content: center;
}

.whitelogo img {
    filter: invert(1);
}
</style>
