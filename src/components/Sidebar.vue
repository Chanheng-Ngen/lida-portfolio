<template>
  <div class="px-8 py-10 flex flex-col gap-10 text-sm font-light tracking-wide">
    <!-- Profile Image -->
    <div class="w-full flex justify-center mb-4">
      <div class="w-48 h-48 rounded-full border-4 border-white overflow-hidden bg-gray-300">
        <img src="../assets/profile.jpg" alt="Profile" class="w-full h-full object-cover">
      </div>
    </div>

    <!-- Contact -->
    <div class="flex flex-col gap-4">
      <h3 class="text-xl font-bold uppercase tracking-widest border-b border-gray-500 pb-2">Contact</h3>
      <div v-for="(item, index) in contactInfo" :key="index" class="flex gap-4 items-start">
        <div class="mt-1">
          <!-- Simple Icon Placeholders -->
          <span v-if="item.icon === 'phone'">📞</span>
          <span v-else-if="item.icon === 'email'">✉️</span>
          <span v-else-if="item.icon === 'location'">📍</span>
        </div>
        <div class="flex-1 break-words">
          <a v-if="item.link" :href="item.link" class="hover:underline">{{ item.value }}</a>
          <span v-else>{{ item.value }}</span>
        </div>
      </div>
    </div>

    <!-- Education -->
    <div class="flex flex-col gap-2">
      <h3 class="text-xl font-bold uppercase tracking-widest border-b border-gray-500 pb-2">Education</h3>
      <p class="font-bold text-lg">{{ education.year }}</p>
      <p class="font-bold">{{ education.school }}</p>
      <p class="opacity-90">{{ education.degree }}</p>
    </div>

    <!-- Language -->
    <div class="flex flex-col gap-2">
      <h3 class="text-xl font-bold uppercase tracking-widest border-b border-gray-500 pb-2">Language</h3>
      <ul class="flex flex-col gap-2 list-disc pl-5">
        <li v-for="lang in languages" :key="lang.name">
          <div class="flex flex-col">
            <span class="font-bold">{{ lang.name }} <span class="font-normal">{{ lang.level }}</span></span>
            <div v-if="lang.stars > 0" class="flex text-yellow-400 text-xs mt-0.5">
               <span v-for="i in 5" :key="i">{{ i <= lang.stars ? '★' : '☆' }}</span> <!-- Simple stars -->
            </div>
          </div>
        </li>
      </ul>
    </div>

    <!-- Technologies -->
    <div class="flex flex-col gap-2">
      <h3 class="text-xl font-bold uppercase tracking-widest border-b border-gray-500 pb-2">Technologies</h3>
      <ul class="list-disc pl-5 flex flex-col gap-1">
        <li v-for="tech in technologies" :key="tech">{{ tech }}</li>
      </ul>
    </div>

    <!-- Experience Reference -->
    <div class="flex flex-col gap-2">
      <h3 class="text-xl font-bold uppercase tracking-widest border-b border-gray-500 pb-2">Experience</h3>
      <p class="font-bold">{{ experienceRef.name }}, <span class="font-normal opacity-90">{{ experienceRef.title }}</span></p>
      <div class="mt-2 text-xs flex flex-col gap-1 opacity-90">
        <p>PHONE | {{ experienceRef.phone }}</p>
        <p>EMAIL | {{ experienceRef.email }}</p>
      </div>
    </div>

  </div>
</template>
<script setup>

const contactInfo = [
  { icon: 'phone', value: '+855 93 688 612' },
  { icon: 'email', value: 'chhenlida08@gmail.com', link: 'mailto:chhenlida08@gmail.com' },
  { icon: 'location', value: '271 Street, Sangkat Boeng Tumpunl, Mean Chey district, Phnom Penh City' }
]

const education = {
  year: '2021 - Now',
  school: 'Institut de Technologie du Cambodge',
  degree: 'Bachelor of information technology and communication'
}

const languages = [
  { name: 'Khmer', level: '(Native language)', stars: 0 }, 
  { name: 'English', level: '', stars: 4 },
  { name: 'French', level: '', stars: 3 } 
]

const technologies = [
  'Svelte', 'Vue.js', 'Laravel', 'Mysql', 'DrawDB', 'MongoDB', 'Nestjs'
]

const experienceRef = {
  name: 'Mr. HOK Tin',
  title: 'Professor at Institute of Technology of Cambodia',
  phone: '+855 866 670 74',
  email: 'hok.tin@itc.edu.kh'
}

</script>
