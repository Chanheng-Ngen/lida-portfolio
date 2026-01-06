<script setup>
import { ExternalLink, Github, Folder } from 'lucide-vue-next';

const projects = [
  {
    title: 'Music Player App',
    description: 'A responsive music player web application delivering a seamless audio experience across devices.',
    tech: ['HTML', 'CSS', 'JavaScript'],
    type: 'Frontend',
  },
  {
    title: 'E-commerce Platform',
    description: 'Full-stack e-commerce solution with Laravel backend and Svelte frontend, handling product management and orders.',
    tech: ['Laravel', 'Svelte', 'MySQL'],
    type: 'Full Stack',
  },
  {
    title: 'Quiz Management System',
    description: 'Online platform for quiz management using NestJS for backend, Svelte for frontend, and GraphQL for API.',
    tech: ['Svelte', 'NestJS', 'GraphQL'],
    type: 'Full Stack',
  },
  {
    title: 'LED Scrolling Text',
    description: 'Desktop application simulating LED text animation using Object-Oriented Programming (OOP) principles.',
    tech: ['Java', 'OOP', 'VS Code'],
    type: 'Desktop App',
  },
  {
    title: 'E-commerce Frontend',
    description: 'Designed modern user interface for an e-commerce platform using Vue.js.',
    tech: ['Vue.js', 'UI Design'],
    type: 'Frontend',
  },
  {
    title: 'E-commerce Frontend',
    description: 'Designed modern user interface for an e-commerce platform using Vue.js.',
    tech: ['Vue.js', 'UI Design'],
    type: 'Frontend',
  }
];
</script>

<template>
  <section id="projects" class="py-20">
    <div class="container mx-auto px-6">
      
      <div class="mb-12">
        <h2 class="text-3xl font-bold text-slate-100 dark:text-white mb-4">Featured Projects</h2>
      </div>

      <div class="grid md:grid-cols-2 lg:grid-cols-3 gap-8">
        <div 
          v-for="(project, index) in projects" 
          :key="index"
          class="bg-slate-900 dark:bg-slate-900 border border-slate-700 dark:border-slate-800 rounded-xl p-8 hover:shadow-xl hover:-translate-y-1 transition-all duration-300 group"
        >
          <div class="flex justify-between items-start mb-6">
            <div class="p-3 bg-blue-200 dark:bg-blue-900/20 rounded-lg text-slate-600 dark:text-blue-400">
               <Folder class="w-6 h-6" />
            </div>
            <div class="flex gap-4 opacity-0 group-hover:opacity-100 transition-opacity">
              <a href="#" class="text-slate-400 hover:text-slate-100 dark:hover:text-white"><Github class="w-5 h-5"/></a>
              <a href="#" class="text-slate-400 hover:text-slate-100 dark:hover:text-white"><ExternalLink class="w-5 h-5"/></a>
            </div>
          </div>
          
          <h3 class="text-xl font-bold text-slate-100 dark:text-white mb-3 group-hover:text-blue-500 dark:group-hover:text-blue-400 transition-colors">
            {{ project.title }}
          </h3>
          
          <p class="text-slate-300 dark:text-slate-400 text-lg leading mb-6 h-20">
            {{ project.description }}
          </p>
          
          <div class="flex flex-wrap gap-2 mt-auto">
            <span 
              v-for="t in project.tech" 
              :key="t"
              class="text-xs font-mono text-slate-100 bg-slate-700 dark:bg-slate-800 px-2 py-1 rounded"
            >
              #{{ t }}
            </span>
          </div>
        </div>
      </div>

    </div>
  </section>
</template>
