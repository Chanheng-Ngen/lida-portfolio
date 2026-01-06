<script setup>
import { ref, onMounted, onUnmounted } from 'vue';
import { Menu, X } from 'lucide-vue-next';

const isMenuOpen = ref(false);
const activeSection = ref('hero');

const navLinks = [
  { name: 'About', href: '#hero' },
  { name: 'Skills', href: '#skills' },
  { name: 'Projects', href: '#projects' },
  { name: 'Experience', href: '#experience' },
  { name: 'Contact', href: '#contact' },
];

const scrollTo = (href) => {
  isMenuOpen.value = false;
  const element = document.querySelector(href);
  if (element) {
    element.scrollIntoView({ behavior: 'smooth' });
  }
};

onMounted(() => {
  const observer = new IntersectionObserver((entries) => {
    entries.forEach(entry => {
      if (entry.isIntersecting) {
        activeSection.value = entry.target.id;
      }
    });
  }, { threshold: 0.5 });

  navLinks.forEach(link => {
    const section = document.querySelector(link.href);
    if (section) observer.observe(section);
  });
});
</script>

<template>
  <div class="fixed top-6 left-0 right-0 z-50 flex justify-center px-4">
    <!-- Floating Glass Island -->
    <nav
      class="bg-white/50 dark:bg-slate-900/80 backdrop-blur-xl border border-white/20 dark:border-white/10 rounded-full px-6 py-3 shadow-2xl flex items-center gap-8 max-w-4xl w-full justify-between transition-all duration-300">

      <!-- Logo -->
      <a href="#" class="text-xl font-bold text-slate-900 dark:text-white tracking-tight shrink-0">
        CL<span class="text-blue-600">.</span>
      </a>

      <!-- Desktop Links -->
      <div class="hidden md:flex items-center gap-2">
        <a v-for="link in navLinks" :key="link.name" @click.prevent="scrollTo(link.href)" href="#"
          class="px-4 py-2 rounded-full text-sm font-medium transition-all duration-300 relative group" :class="[
            activeSection === link.href.substring(1)
              ? 'text-white'
              : 'text-slate-300 dark:text-slate-200 hover:text-slate-900 dark:hover:text-white'
          ]">
          <!-- Active Background Pill -->
          <span v-if="activeSection === link.href.substring(1)"
            class="absolute inset-0 bg-blue-500 rounded-full -z-10 shadow-md"></span>

          <!-- Hover Effect -->
          <span v-else
            class="absolute inset-0 bg-slate-100 dark:bg-white/5 rounded-full scale-0 group-hover:scale-100 transition-transform -z-10"></span>

          {{ link.name }}
        </a>
      </div>

      <!-- CTA Button -->
      <a href="#contact"
        class="hidden md:block bg-slate-900 dark:bg-white text-white dark:text-slate-900 px-6 py-2 rounded-full text-sm font-bold hover:scale-105 transition-transform">
        Hire Me
      </a>

      <!-- Mobile Menu Toggle -->
      <button class="md:hidden text-slate-900 dark:text-white" @click="isMenuOpen = !isMenuOpen">
        <Menu v-if="!isMenuOpen" />
        <X v-else />
      </button>
    </nav>

    <!-- Mobile Menu Container -->
    <div v-if="isMenuOpen"
      class="absolute top-full mt-4 left-4 right-4 bg-white dark:bg-slate-900 p-6 rounded-3xl shadow-2xl border border-slate-200 dark:border-slate-800 flex flex-col gap-4 md:hidden">
      <a v-for="link in navLinks" :key="link.name" @click.prevent="scrollTo(link.href)" href="#"
        class="text-lg font-medium text-slate-600 dark:text-slate-300 p-2"
        :class="{ 'text-blue-600 dark:text-blue-400 font-bold': activeSection === link.href.substring(1) }">
        {{ link.name }}
      </a>
    </div>
  </div>
</template>
