<template>
  <section id="contact" class="py-12 bg-[#0f172a] text-white relative overflow-hidden border-t border-slate-800">
    <div
      class="absolute top-1/2 right-0 -translate-y-1/2 w-[500px] h-[500px] bg-blue-600/10 rounded-full blur-[120px] pointer-events-none">
    </div>
    <div
      class="absolute bottom-0 left-0 w-[300px] h-[300px] bg-cyan-500/10 rounded-full blur-[100px] pointer-events-none">
    </div>

    <div class="container mx-auto px-6 max-w-6xl relative z-10">

      <div class="grid lg:grid-cols-2 gap-12 lg:gap-16 items-start">

        <!-- Left Side: Header & Socials -->
        <div class="space-y-8">
          <div>
            <h2 class="text-3xl md:text-4xl font-bold mb-6">
              <span class="bg-clip-text text-transparent bg-gradient-to-r from-blue-400 to-sky-300">Let's Connect</span>
            </h2>
            <p class="text-slate-400 text-lg leading-relaxed max-w-md">
              I'm always open to discussing new projects, creative ideas, or opportunities to be part of your vision.
            </p>
          </div>

          <!-- Social Buttons -->
          <div class="flex flex-wrap gap-4">
            <a href="#"
              class="flex items-center gap-3 px-6 py-3 rounded-full bg-slate-800/50 border border-slate-700 hover:border-sky-500 hover:bg-slate-800 transition-all group">
              <Linkedin class="w-5 h-5 text-slate-400 group-hover:text-white" />
              <span class="font-medium text-slate-300 group-hover:text-white">LinkedIn</span>
            </a>
            <a href="#"
              class="flex items-center gap-3 px-6 py-3 rounded-full bg-slate-800/50 border border-slate-700 hover:border-sky-500 hover:bg-slate-800 transition-all group">
              <Github class="w-5 h-5 text-slate-400 group-hover:text-white" />
              <span class="font-medium text-slate-300 group-hover:text-white">GitHub</span>
            </a>
            <a href="https://t.me/yourusername"
              class="flex items-center gap-3 px-6 py-3 rounded-full bg-slate-800/50 border border-slate-700 hover:border-sky-500 hover:bg-slate-800 transition-all group">
              <svg class="w-5 h-5 text-slate-400 group-hover:text-white" fill="currentColor" viewBox="0 0 24 24">
                <path
                  d="M12 0C5.373 0 0 5.373 0 12s5.373 12 12 12 12-5.373 12-12S18.627 0 12 0zm5.894 8.221l-1.97 9.28c-.145.658-.537.818-1.084.508l-3-2.21-1.446 1.394c-.14.18-.357.295-.6.295-.002 0-.003 0-.005 0l.213-3.054 5.56-5.022c.24-.213-.054-.334-.373-.121l-6.869 4.326-2.96-.924c-.64-.203-.658-.64.135-.954l11.566-4.458c.538-.196 1.006.128.832.941z" />
              </svg>
              <span class="font-medium text-slate-300 group-hover:text-white">Telegram</span>
            </a>
            <a href="mailto:chhenlida04@gmail.com"
              class="flex items-center gap-3 px-6 py-3 rounded-full bg-slate-800/50 border border-slate-700 hover:border-sky-500 hover:bg-slate-800 transition-all group">
              <Mail class="w-5 h-5 text-slate-400 group-hover:text-white" />
              <span class="font-medium text-slate-300 group-hover:text-white">Email</span>
            </a>
          </div>
        </div>

        <!-- Right Side: Form -->
        <div class="bg-transparent">
          <form class="space-y-6" @submit.prevent="handleSubmit">
            <div class="space-y-2">
              <label class="sr-only">Your Name</label>
              <input v-model="form.name" required type="text" placeholder="Your Name"
                class="w-full px-6 py-4 bg-[#1e293b] border border-slate-700 rounded-xl focus:border-sky-500 focus:ring-1 focus:ring-sky-500 outline-none transition-all placeholder-slate-500 text-white" />
            </div>

            <div class="space-y-2">
              <label class="sr-only">Your Email</label>
              <input v-model="form.email" required type="email" placeholder="Your Email"
                class="w-full px-6 py-4 bg-[#1e293b] border border-slate-700 rounded-xl focus:border-sky-500 focus:ring-1 focus:ring-sky-500 outline-none transition-all placeholder-slate-500 text-white" />
            </div>

            <div class="space-y-2">
              <label class="sr-only">Your Message</label>
              <textarea v-model="form.message" required rows="5" placeholder="Your Message"
                class="w-full px-6 py-4 bg-[#1e293b] border border-slate-700 rounded-xl focus:border-sky-500 focus:ring-1 focus:ring-sky-500 outline-none transition-all placeholder-slate-500 text-white resize-none"></textarea>
            </div>

            <button :disabled="isSubmitting"
              class="w-full py-4 bg-white/10 backdrop-blur-lg hover:bg-white/20 text-white font-bold rounded-xl transition-all duration-300 border border-white/20 shadow-xl flex items-center justify-center gap-2 transform hover:-translate-y-1 disabled:opacity-50 disabled:cursor-not-allowed disabled:transform-none">
              <span v-if="!isSubmitting">Send Message</span>
              <span v-else class="flex items-center gap-2">
                <Loader2 class="w-5 h-5 animate-spin" />
                Sending...
              </span>
            </button>
          </form>
        </div>
      </div>
    </div>
    <footer
      class="px-12 mt-24 pt-8 border-t border-slate-800 flex flex-col md:flex-row justify-between items-center gap-4 text-slate-500 text-sm">
      <p>© 2026 Chhen Lida. All rights reserved.</p>
    </footer>
  </section>
</template>
<script setup>
import { ref } from 'vue';
import { Linkedin, Github, Twitter, Mail, Send, Loader2 } from 'lucide-vue-next';
import emailjs from '@emailjs/browser';

const isSubmitting = ref(false);
const form = ref({
  name: '',
  email: '',
  message: ''
});

const handleSubmit = async () => {
  isSubmitting.value = true;
  try {
    const result = await emailjs.send(
      import.meta.env.VITE_EMAILJS_SERVICE_ID,
      import.meta.env.VITE_EMAILJS_TEMPLATE_ID,     
      {
        from_name: form.value.name,
        from_email: form.value.email,
        message: form.value.message,
        to_email: import.meta.env.VITE_EMAILJS_TO_EMAIL
      },
      import.meta.env.VITE_EMAILJS_PUBLIC_KEY       
    );
    
    console.log('SUCCESS!', result.text);
    alert('Message sent successfully!');
    form.value = { name: '', email: '', message: '' };
  } catch (error) {
    console.error('FAILED...', error);
    alert('Failed to send message. Please try again.');
  } finally {
    isSubmitting.value = false;
  }
};
</script>
