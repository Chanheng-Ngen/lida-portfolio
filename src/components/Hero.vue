
<template>
  <section id="hero" class="min-h-screen flex items-center pt-20 relative overflow-hidden">
    <!-- Creative Background Elements -->
    <div class="absolute top-20 left-10 w-24 h-24 bg-blue-500/20 rounded-full blur-2xl animate-float delay-100"></div>
    <div class="absolute bottom-20 right-10 w-32 h-32 bg-purple-500/20 rounded-full blur-2xl animate-float delay-700"></div>
    <div class="absolute top-1/2 left-1/2 -translate-x-1/2 -translate-y-1/2 w-[800px] h-[800px] border border-slate-200 dark:border-slate-800 rounded-full opacity-20 animate-[spin_60s_linear_infinite]"></div>
    
    <div class="container mx-auto px-6 grid lg:grid-cols-2 gap-16 items-center relative z-10">
      
      <!-- Text Content -->
      <div class="space-y-8 order-2 lg:order-1">
        <div class="space-y-4">
          <!-- Animated Badge -->
          <div class="inline-flex items-center gap-2 px-3 py-1 rounded-full bg-blue-600/10 border border-blue-600/20 text-blue-600 dark:text-blue-400 text-xs font-bold uppercase tracking-widest w-fit animate-fade-in-up">
             <span class="relative flex h-2 w-2">
               <span class="animate-ping absolute inline-flex h-full w-full rounded-full bg-blue-400 opacity-75"></span>
               <span class="relative inline-flex rounded-full h-2 w-2 bg-blue-500"></span>
             </span>
             Hello, I'm
          </div>

          <h1 class="text-3xl lg:text-6xl font-bold text-slate-100 dark:text-white leading-tight animate-fade-in-up delay-100">
            Chhen Lida
          </h1>
          
          <!-- Typing Effect -->
          <div class="h-8 animate-fade-in-up delay-200">
            <span class="text-2xl lg:text-3xl font-medium bg-clip-text text-transparent bg-gradient-to-r from-blue-600 to-purple-600 dark:from-blue-400 dark:to-purple-400">
              {{ currentRole }}<span class="animate-blink text-slate-900 dark:text-white">|</span>
            </span>
          </div>

          <p class="text-xl text-slate-600 dark:text-slate-400 leading-relaxed max-w-xl animate-fade-in-up delay-300">
             Five-year IT student blending technical expertise with creative problem solving. I build accessible, pixel-perfect, and performant web experiences.
          </p>
        </div>

        <div class="flex flex-wrap gap-4 animate-fade-in-up delay-500">
          <a href="#projects" class="group relative px-8 py-3 border-2 border-blue-500 text-blue-600 dark:text-blue-400 dark:border-blue-400 rounded-full font-medium overflow-hidden transition-all duration-300 hover:text-white hover:scale-105 active:scale-95">
          <div class="absolute inset-0 bg-blue-500 dark:bg-blue-500 -translate-x-full group-hover:translate-x-0 transition-transform duration-300"></div>
          <span class="relative flex items-center gap-2">
            View Projects 
            <ArrowRight class="w-4 h-4 group-hover:translate-x-1 transition-transform duration-300" />
          </span>
        </a>
        <a href="https://docs.google.com/document/d/13HNFPamLG5BthNA91SuP8x4D2mEmvhzvBMOv_LP_3MI/edit?usp=sharing" class="group relative px-8 py-3 border-2 border-slate-600 dark:border-slate-400 text-slate-700 dark:text-slate-300 rounded-full font-medium overflow-hidden transition-all duration-300 hover:text-white dark:hover:text-slate-900 hover:scale-105 active:scale-95">
          <div class="absolute inset-0 bg-slate-700 dark:bg-slate-300 -translate-x-full group-hover:translate-x-0 transition-transform duration-300"></div>
          <span class="relative flex items-center gap-2">Download CV
          <Download class="w-4 h-4 group-hover:translate-x-1 transition-transform duration-300" />
          </span>
        </a>
        </div>
      </div>

      <!-- Hero Visual -->
      <div class="relative order-1 lg:order-2 flex justify-center lg:justify-end animate-fade-in-left delay-500">
         <div class="relative w-72 h-72 md:w-96 md:h-96">
            <!-- Decorative Ring -->
            <div class="absolute inset-0 border-2 border-blue-600/20 rounded-full scale-110"></div>
            <div class="absolute inset-0 border border-slate-200 dark:border-white/10 rounded-full scale-125 border-dashed animate-[spin_60s_linear_infinite]"></div>
            
            <!-- Image -->
            <div class="absolute inset-0 rounded-full overflow-hidden border-8 border-white dark:border-slate-800 shadow-2xl">
              <img src="../assets/lida_profile_i.jpg" alt="Chhen Lida" class="w-full h-full object-cover">
            </div>

            <!-- Floating Badge -->
            <div class="absolute -bottom-6 -left-6 bg-slate-300 dark:bg-slate-800 p-4 rounded-xl shadow-xl flex items-center gap-3 border border-slate-100 dark:border-slate-700">
               <div class="w-3 h-3 bg-green-500 rounded-full animate-pulse"></div>
               <div>
                 <p class="text-xs text-slate-400 font-bold uppercase">Status</p>
                 <p class="text-sm font-bold text-slate-900 dark:text-white">Open to Work</p>
               </div>
            </div>
         </div>
      </div>

    </div>
  </section>
</template>
<script setup>
import { ref, onMounted } from 'vue';
import { ArrowRight, ArrowUpDown, Download } from 'lucide-vue-next';

const roles = ["Full Stack Developer", "UI/UX Designer", "Data Analyst"];
const currentRole = ref("");
const roleIndex = ref(0);
const charIndex = ref(0);
const isDeleting = ref(false);
const typingSpeed = ref(100);

const typeEffect = () => {
  const currentFullRole = roles[roleIndex.value];
  
  if (isDeleting.value) {
    currentRole.value = currentFullRole.substring(0, charIndex.value - 1);
    charIndex.value--;
    typingSpeed.value = 50;
  } else {
    currentRole.value = currentFullRole.substring(0, charIndex.value + 1);
    charIndex.value++;
    typingSpeed.value = 100;
  }

  if (!isDeleting.value && charIndex.value === currentFullRole.length) {
    isDeleting.value = true;
    typingSpeed.value = 2000; 
  } else if (isDeleting.value && charIndex.value === 0) {
    isDeleting.value = false;
    roleIndex.value = (roleIndex.value + 1) % roles.length;
    typingSpeed.value = 500; 
  }

  setTimeout(typeEffect, typingSpeed.value);
};

onMounted(() => {
  typeEffect();
});
</script>
<style scoped>
@keyframes blink {
  0%, 100% { opacity: 1; }
  50% { opacity: 0; }
}

.animate-blink {
  animation: blink 1s infinite;
}

@keyframes float {
  0%, 100% { transform: translateY(0); }
  50% { transform: translateY(-20px); }
}

.animate-float {
  animation: float 6s ease-in-out infinite;
}

@keyframes fadeInUp {
  from {
    opacity: 0;
    transform: translateY(20px);
  }
  to {
    opacity: 1;
    transform: translateY(0);
  }
}

.animate-fade-in-up {
  opacity: 0;
  animation: fadeInUp 0.8s ease-out forwards;
}

@keyframes fadeInLeft {
  from {
    opacity: 0;
    transform: translateX(20px);
  }
  to {
    opacity: 1;
    transform: translateX(0);
  }
}

.animate-fade-in-left {
  opacity: 0;
  animation: fadeInLeft 0.8s ease-out forwards;
}

.delay-100 { animation-delay: 0.1s; }
.delay-200 { animation-delay: 0.2s; }
.delay-300 { animation-delay: 0.3s; }
.delay-500 { animation-delay: 0.5s; }
.delay-700 { animation-delay: 0.7s; }
</style>
