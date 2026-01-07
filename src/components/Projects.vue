<template>
  <section id="projects" class="py-20">
    <div class="container mx-auto px-6">
      <div class="mb-12">
        <h2 class="text-2xl font-bold text-slate-100 dark:text-white mb-4">
          Featured Projects
        </h2>
      </div>

      <div class="grid md:grid-cols-2 lg:grid-cols-3 gap-8">
        <div
          v-for="(project, index) in paginatedProjects"
          :key="index"
          class="bg-slate-800 dark:bg-slate-800 rounded-xl overflow-hidden shadow-lg hover:shadow-2xl hover:scale-[1.02] cursor-pointer transition-all duration-300 group"
        >
          <!-- Image Header -->
          <div class="relative h-36 overflow-hidden">
            <img
              src="https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcQmH79Xg2-Ki0mH8L3d8cXIuGLwWKzH3hu73A&s"
              alt="Project"
              class="w-full h-full object-cover opacity-50"
            />
            <div
              class="absolute top-4 right-4 flex gap-3 opacity-0 translate-y-2 group-hover:opacity-100 group-hover:translate-y-0 transition-all duration-300"
            >
              <!-- GitHub repo -->
              <a
                v-if="project.github"
                :href="project.github"
                target="_blank"
                rel="noopener noreferrer"
                class="p-2 bg-white/15 backdrop-blur-sm rounded-full text-white hover:bg-blue-500 transition-all"
              >
                <Github class="w-5 h-5" />
              </a>

              <!-- Live hosted project -->
              <a
                v-if="project.live"
                :href="project.live"
                target="_blank"
                rel="noopener noreferrer"
                class="p-2 bg-white/15 backdrop-blur-sm rounded-full text-white hover:bg-blue-500 transition-all"
              >
                <ExternalLink class="w-5 h-5" />
              </a>
            </div>
          </div>

          <!-- Content -->
          <div class="p-6">
            <h3 class="text-xl font-bold text-slate-200 dark:text-white mb-3">
              {{ project.title }}
            </h3>

            <p
              class="text-slate-400 text-lg dark:text-slate-300 mb-4 line-clamp-2"
            >
              {{ project.description }}
            </p>

            <div class="flex flex-wrap gap-2">
              <span
                v-for="t in project.tech"
                :key="t"
                class="text-xs font-medium text-slate-300 dark:text-slate-300 border border-slate-500 dark:border-slate-600 px-3 py-1 rounded-full"
              >
                {{ t }}
              </span>
            </div>
          </div>
        </div>
      </div>

      <!-- Pagination -->
      <div class="flex justify-end items-center gap-2 mt-12">
        <button
          @click="prevPage"
          :disabled="currentPage === 1"
          class="p-2 rounded-lg bg-slate-800 text-slate-300 hover:bg-slate-700 disabled:opacity-50 disabled:cursor-not-allowed transition-all"
        >
          <ChevronLeft class="w-5 h-5" />
        </button>

        <button
          v-for="page in totalPages"
          :key="page"
          @click="goToPage(page)"
          :class="[
            'px-4 py-2 rounded-lg transition-all',
            currentPage === page
              ? 'bg-blue-500 text-white'
              : 'bg-slate-800 text-slate-300 hover:bg-slate-700',
          ]"
        >
          {{ page }}
        </button>

        <button
          @click="nextPage"
          :disabled="currentPage === totalPages"
          class="p-2 rounded-lg bg-slate-800 text-slate-300 hover:bg-slate-700 disabled:opacity-50 disabled:cursor-not-allowed transition-all"
        >
          <ChevronRight class="w-5 h-5" />
        </button>
      </div>
    </div>
  </section>
</template>
<script setup>
import { ref, computed } from "vue";
import {
  ExternalLink,
  Github,
  Folder,
  ChevronLeft,
  ChevronRight,
} from "lucide-vue-next";

const currentPage = ref(1);
const itemsPerPage = 6;
const projects = [
  {
    title: "Music Player App",
    description:
      "A responsive music player web application delivering a seamless audio experience across devices.",
    tech: ["HTML", "CSS", "JavaScript"],
    type: "Frontend",
  },

  {
    title: "E-commerce Platform",
    description:
      "Full-stack e-commerce solution with Laravel backend and Svelte frontend, handling product management and orders.",
    tech: ["Laravel", "Svelte", "MySQL"],
    type: "Full Stack",
    github: "https://github.com/NaySovannarith/Tech-Compare", 
    live: "https://tech-compare-dun.vercel.app",
  },

  {
    title: "Quiz Management System",
    description:
      "Online platform for quiz management using NestJS for backend, Svelte for frontend, and GraphQL for API.",
    tech: ["Svelte", "NestJS", "GraphQL"],
    type: "Full Stack",
      github: {
      frontend: 'https://github.com/chhenlida/Kquiz',
      backend: 'https://github.com/chhenlida/Quiz-Backend'
    },
  },
  {
    title: "LED Scrolling Text",
    description:
      "Desktop application simulating LED text animation using Object-Oriented Programming (OOP) principles.",
    tech: ["Java", "OOP", "VS Code"],
    type: "Desktop App",
  },
  {
    title: "E-commerce Frontend",
    description:
      "Designed modern user interface for an e-commerce platform using Vue.js.",
    tech: ["Vue.js", "UI Design"],
    type: "Frontend",
  },
  {
    title: "E-commerce Frontend",
    description:
      "Designed modern user interface for an e-commerce platform using Vue.js.",
    tech: ["Vue.js", "UI Design"],
    type: "Frontend",
  },
  {
    title: "E-commerce Platform",
    description:
      "Full-stack e-commerce solution with Laravel backend and Svelte frontend, handling product management and orders.",
    tech: ["Laravel", "Svelte", "MySQL"],
    type: "Full Stack",
  },
  {
    title: "Quiz Management System",
    description:
      "Online platform for quiz management using NestJS for backend, Svelte for frontend, and GraphQL for API.",
    tech: ["Svelte", "NestJS", "GraphQL"],
    type: "Full Stack",
  },
  {
    title: "LED Scrolling Text",
    description:
      "Desktop application simulating LED text animation using Object-Oriented Programming (OOP) principles.",
    tech: ["Java", "OOP", "VS Code"],
    type: "Desktop App",
  },
  {
    title: "E-commerce Frontend",
    description:
      "Designed modern user interface for an e-commerce platform using Vue.js.",
    tech: ["Vue.js", "UI Design"],
    type: "Frontend",
  },
  {
    title: "E-commerce Frontend",
    description:
      "Designed modern user interface for an e-commerce platform using Vue.js.",
    tech: ["Vue.js", "UI Design"],
    type: "Frontend",
  },
];

const totalPages = computed(() => Math.ceil(projects.length / itemsPerPage));

const paginatedProjects = computed(() => {
  const start = (currentPage.value - 1) * itemsPerPage;
  const end = start + itemsPerPage;
  return projects.slice(start, end);
});

const goToPage = (page) => {
  currentPage.value = page;
};

const nextPage = () => {
  if (currentPage.value < totalPages.value) {
    currentPage.value++;
  }
};

const prevPage = () => {
  if (currentPage.value > 1) {
    currentPage.value--;
  }
};
</script>
