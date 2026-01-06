<template>
  <section id="skills" class="py-20 bg-black/20 dark:bg-black/20">
    <div class="container mx-auto px-6">
      
      <div class="mb-16 text-center max-w-2xl mx-auto">
        <h2 class="text-3xl font-bold text-slate-100 dark:text-white mb-4">Technical Proficiency</h2>
        <p class="text-lg text-slate-400 dark:text-slate-400">
          A comprehensive toolkit of modern technologies and methodologies I use to build scalable solutions.
        </p>
      </div>

      <div class="grid md:grid-cols-2 gap-12">
        <!-- Tech Skills -->
        <div   class="space-y-8">
           <div v-for="group in techSkills" :key="group.category">
              <h3 class="text-lg font-bold text-slate-100 dark:text-white mb-4 flex items-center gap-2">
                 {{ group.category }}
              </h3>
              <div class="flex flex-wrap gap-3">
                 <div 
                   v-for="item in group.items" 
                   :key="item.name"
                   class="flex items-center gap-2 px-4 py-2 bg-slate-800 dark:bg-slate-800 border border-blue-900 dark:border-slate-700 rounded-lg text-sm font-medium text-slate-100 dark:text-slate-300"
                 >
                   <img :src="item.icon" :alt="item.name" class="w-5 h-5 object-contain" />
                   {{ item.name }}
                 </div>
              </div>
           </div>
        </div>

        <!-- Soft Skills -->
        <div class="bg-slate-900 dark:bg-slate-900 text-white rounded-3xl p-10 h-full relative overflow-hidden">
           <div class="absolute top-0 right-0 w-64 h-64 bg-white/10 rounded-full -translate-y-1/2 translate-x-1/3 blur-3xl"></div>
           
           <h3 class="text-2xl font-bold mb-8 relative z-10">Soft Skills</h3>
           <div class="space-y-4 relative z-10">
              <div 
                v-for="skill in softSkills" 
                :key="skill"
                class="flex items-center gap-3"
              >
                <CheckCircle2 class="text-blue-200 w-5 h-5 flex-shrink-0" />
                <span class="font-medium text-blue-50 text-lg">{{ skill }}</span>
              </div>
           </div>
        </div>
      </div>

    </div>
  </section>
</template>
<script setup>
import { CheckCircle2 } from 'lucide-vue-next';

// Helper to get Devicon URL
const getIcon = (name) => `https://cdn.jsdelivr.net/gh/devicons/devicon/icons/${name}/${name}-original.svg`;

const techSkills = [
  { 
    category: 'Frontend', 
    items: [
      { name: 'Vue.js', icon: getIcon('vuejs') },
      { name: 'Svelte', icon: getIcon('svelte') },
      { name: 'CSS3', icon: getIcon('css3') },
      { name: 'Tailwind CSS', icon: 'https://cdn.jsdelivr.net/gh/devicons/devicon@latest/icons/tailwindcss/tailwindcss-original.svg' },
      { name: 'Bootstrap', icon: 'https://cdn.jsdelivr.net/gh/devicons/devicon@latest/icons/bootstrap/bootstrap-plain.svg' },
      { name: 'HTML5', icon: getIcon('html5') },
      { name: 'JavaScript', icon: getIcon('javascript') }
    ] 
  },
  { 
    category: 'Backend', 
    items: [
      { name: 'NestJS', icon: 'https://cdn.jsdelivr.net/gh/devicons/devicon@latest/icons/nestjs/nestjs-original.svg' },
      { name: 'Laravel', icon: 'https://cdn.jsdelivr.net/gh/devicons/devicon@latest/icons/laravel/laravel-original.svg' },
      { name: 'Node.js', icon: getIcon('nodejs') },
      { name: 'PHP', icon: getIcon('php') }
    ] 
  },
  { 
    category: 'Database', 
    items: [
      { name: 'MongoDB', icon: getIcon('mongodb') },
      { name: 'MySQL', icon: getIcon('mysql') },
      { name: 'DrawDB', icon: 'https://avatars.githubusercontent.com/u/142609099?s=200&v=4' } 
    ] 
  },
  { 
    category: 'Tools', 
    items: [
      { name: 'Git', icon: getIcon('git') },
      { name: 'VS Code', icon: getIcon('vscode') },
      { name: 'Postman', icon: getIcon('postman') }
    ] 
  },
  { 
    category: 'Design', 
    items: [
      { name: 'UI/UX Design', icon: getIcon('figma') },
      { name: 'Canva', icon: 'https://cdn.jsdelivr.net/gh/devicons/devicon@latest/icons/canva/canva-original.svg' },
    ] 
  }
];

const softSkills = [
  'Independent Problem Solving',
  'Team Collaboration',
  'Creativity & Innovation',
  'Continuous Learning',
  'Adaptability',
  'Time Management'
];
</script>
