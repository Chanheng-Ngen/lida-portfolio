<template>
  <div class="bg-slate-900 min-h-screen text-slate-200 selection:bg-emerald-500/30 selection:text-emerald-200 transition-colors duration-500">
     <!-- Grid Background Pattern (FROM ANTIGRAVITY) -->
    <div class="fixed inset-0 z-0 pointer-events-none">
       <!-- Gradient Orb 1 (Modified for Emerald/Slate Compatibility) -->
       <div class="absolute top-[-10%] left-[-10%] w-[500px] h-[500px] rounded-full bg-emerald-500/10 blur-[100px] mix-blend-screen animate-blob"></div>
       <!-- Gradient Orb 2 -->
       <div class="absolute top-[20%] right-[-10%] w-[400px] h-[400px] rounded-full bg-blue-600/10 blur-[100px] mix-blend-screen animate-blob animation-delay-2000"></div>
       <!-- Background Grid -->
       <div class="absolute inset-0 bg-[linear-gradient(to_right,#80808012_1px,transparent_1px),linear-gradient(to_bottom,#80808012_1px,transparent_1px)] bg-[size:100px_100px] opacity-100"></div>
    </div>

    <!-- Content Wrapper to ensure z-index above background -->
    <div class="relative z-10">
      <Navbar />
      <main>
        <Hero />
        <TechStack />
        <Projects />
        <Experience />
        <Contact />
      </main>
    </div>
  </div>
</template>
<script setup>
import Navbar from './components/Navbar.vue'
import Hero from './components/Hero.vue'
import TechStack from './components/TechStack.vue'
import Projects from './components/Projects.vue'
import Experience from './components/Experience.vue'
import Contact from './components/Contact.vue'
</script>
<style>
@import url('https://fonts.googleapis.com/css2?family=Outfit:wght@300;400;500;600;700;800&display=swap');

html {
  scroll-behavior: smooth;
}

body {
  font-family: 'Outfit', sans-serif;
  @apply bg-slate-900 text-slate-200; 
}

/* Custom Animation Utility Classes */
@keyframes blob {
  0% { transform: translate(0px, 0px) scale(1); }
  33% { transform: translate(30px, -50px) scale(1.1); }
  66% { transform: translate(-20px, 20px) scale(0.9); }
  100% { transform: translate(0px, 0px) scale(1); }
}

.animate-blob {
  animation: blob 10s infinite;
}

.animation-delay-2000 {
  animation-delay: 2s;
}

/* Custom Scrollbar */
::-webkit-scrollbar {
  width: 10px;
}

::-webkit-scrollbar-track {
  @apply bg-white dark:bg-slate-900;
}

::-webkit-scrollbar-thumb {
  @apply bg-slate-300 dark:bg-slate-800 rounded-full border border-slate-200 dark:border-slate-700;
}

::-webkit-scrollbar-thumb:hover {
  @apply bg-slate-400 dark:bg-slate-700;
}
</style>
