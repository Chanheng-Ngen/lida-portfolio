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
              :src="project.image"
              :alt="project.title"
              class="w-full h-full object-cover opacity-50 group-hover:opacity-70 transition-all duration-300"
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
    title: "E-commerce Platform",
    description:
      "A full-stack web platform for comparing technologies and products, built with a Laravel backend and Svelte frontend. It supports product management, detailed comparisons, and user-friendly browsing.",
    tech: ["Laravel", "Svelte", "MySQL"],
    type: "Full Stack",
    image: '/projects/Tech.png',
    github: "https://github.com/NaySovannarith/Tech-Compare",
    live: "https://tech-compare-dun.vercel.app",
  },

  {
    title: "Quiz Management System",
    description:
      "Online platform for quiz management using NestJS for backend, Svelte for frontend, and GraphQL for API.",
    tech: ["Svelte", "NestJS", "GraphQL"],
    type: "Full Stack",
    image: '/projects/Quiz.jpg',
    github: "https://github.com/chhenlida/Kquiz",
  },
  {
    title: "Book Tracking System",
    description:
      "A full-stack web application built with Svelte and Laravel, featuring a RESTful API to manage books, users, and borrowing records with a clean, modern user interface.",
    tech: ["Svelte", "NestJS", "PostgreSQL"],
    type: "Full Stack",
    image: '/projects/Book.png',
    github: "https://github.com/PhearakreachPR/BOOK_TRACKING_SYSTEM_FRONTEND",
  },
  {
    title: "E-commerce Platform",
    description:
      "E-commerce, short for electronic commerce, involves the online sale of computers and related services.",
    tech: ["Vue.js", "UI Design"],
    type: "Frontend",
    image: '/projects/Computer.png',
    github: "https://github.com/Panhariddh/E-Commerce",
  },

   {
    title: "Music Player App",
    description:
      "A responsive music player web application delivering a seamless audio experience across devices.",
    tech: ["HTML", "CSS", "JavaScript"],
    type: "Frontend",
    image: '/projects/Artist.png',
    github: "https://github.com/ChhayMonyneath123/Project123",
  },
 
  {
    title: "Pet Care Mobile App",
    description:
      "A mobile application with a modern and user-friendly interface for pet care services, developed using Flutter.",
    tech: ["Dart", "Flutter"],
    type: "Frontend",
    image: '/projects/PetCare.png',
    github: "https://github.com/NaySovannarith/PET-CARE",
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
