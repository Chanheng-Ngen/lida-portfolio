<template>
  <div class="flex flex-col h-full">
    <!-- Blue Header Section for Name -->
    <div class="bg-[#0B2447] text-white pt-20 pb-10 px-0 md:-ml-0">
      <div class="flex flex-col justify-end h-32 uppercase ps-4">
        <h1 class="text-5xl font-extrabold tracking-wider leading-tight">
          CHHEN LIDA
        </h1>
        <h2 class="text-xl font-light tracking-widest mt-2 opacity-90">
          FULL STACK DEVELOPER
        </h2>
      </div>
    </div>

    <!-- White Content Section -->
    <div class="bg-white flex-1 p-8 text-gray-800 flex flex-col gap-8">
      <!-- About Me -->
      <div>
        <div
          class="bg-[#0B2447] text-white py-2 px-8 rounded-full inline-block mb-4 font-bold tracking-widest text-lg uppercase shadow-lg"
        >
          About Me
        </div>
        <p class="text-gray-700 leading-relaxed text-sm text-justify">
          Five-year IT student with experience in both front-end and back-end
          development. Skilled in working independently and collaboratively in
          team environments. Passionate about creativity in problem-solving and
          committed to building efficient, user-centered solutions. Continuously
          learning and adapting to new technologies in the software development
          field.
        </p>
      </div>

      <!-- Experience -->
      <div>
        <div
          class="bg-[#0B2447] text-white py-2 px-8 rounded-full inline-block mb-6 font-bold tracking-widest text-lg uppercase shadow-lg"
        >
          Experience
        </div>

        <div
          class="ml-2 border-l-2 border-gray-800 pl-6 flex flex-col gap-6 relative"
        >
          <!-- Project Experience -->
          <div class="relative">
            <div
              class="absolute -left-[31px] top-1.5 w-4 h-4 rounded-full bg-gray-800"
            ></div>
            <h3 class="font-bold text-lg mb-2">Project Experience</h3>
            <ul class="list-disc pl-5 text-sm space-y-2 text-gray-700">
              <li>
                <span class="font-bold text-black">Music Player App</span> -
                Created a responsive web music player using HTML, CSS,
                JavaScript.
              </li>
              <li>
                <span class="font-bold text-black">LED Scrolling Text</span> -
                Simulated LED text animation using Java OOP in Visual Studio
                Code.
              </li>
              <li>
                <span class="font-bold text-black">E-commerce Website</span>
                Developed core features with Laravel and Svelte, including
                product and order management.
              </li>
              <li>
                <span class="font-bold text-black"
                  >E-commerce Website (Frontend)</span
                >
                - Designed user interface using Vue.
              </li>
              <li>
                <span class="font-bold text-black"
                  >Online platform for Quiz Management System</span
                >
                using svelte for frontend and Nestjs for backend and GraphQL for
                API.
              </li>
              <li>
                Attending
                <span class="font-bold text-black">Sister of Code</span> 18 week
                course in digital skills and coding.
              </li>
            </ul>
          </div>

          <!-- Work Experience -->
          <div class="relative">
            <div
              class="absolute -left-[31px] top-1.5 w-4 h-4 rounded-full bg-gray-800"
            ></div>
            <h3 class="font-bold text-lg mb-2">Work Experience</h3>
            <ul class="list-disc pl-5 text-sm space-y-2 text-gray-700">
              <li>
                Work as a teacher at
                <span class="font-bold text-black">Start Up Community(SUC)</span
                >. Duration November 2022- June 2023.
              </li>
              <li>
                Teaching Math for Vietnam scholarship at
                <span class="font-bold text-black">Phoura Y.</span>
              </li>
              <li>
                Work as a Graphic Designer for 3 months at
                <span class="font-bold text-black">RYL</span>
              </li>
            </ul>
          </div>

          <!-- Volunteer -->
          <div class="relative">
            <div
              class="absolute -left-[31px] top-1.5 w-4 h-4 rounded-full bg-gray-800"
            ></div>
            <h3 class="font-bold text-lg mb-2">Volunteer</h3>
            <ul class="list-disc pl-5 text-sm space-y-4 text-gray-700">
              <li>
                <span class="font-bold text-black">Book faire</span> event for 3
                times (2023 and 2025)
                <br />
              </li>
              <li>
                <span class="font-bold text-black">Preah Sorya group</span> for
                the Ten thousand condolences 7th event (2024) and 8th (2025)
                work as Graphic Designer
                <br />
              </li>
              <li>
                <span class="font-bold text-black">RYL</span> Season 12 event
                <br />
              </li>
            </ul>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>
