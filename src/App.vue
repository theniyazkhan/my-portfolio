<script setup>
import { ref, onMounted } from 'vue'

const isDark = ref(false)

// Optional: Check local storage or system preference on mount
onMounted(() => {
  if (localStorage.theme === 'dark' || (!('theme' in localStorage) && window.matchMedia('(prefers-color-scheme: dark)').matches)) {
    isDark.value = true
    document.documentElement.classList.add('dark')
  }
})

const toggleDarkMode = () => {
  isDark.value = !isDark.value
  if (isDark.value) {
    document.documentElement.classList.add('dark')
    localStorage.theme = 'dark'
  } else {
    document.documentElement.classList.remove('dark')
    localStorage.theme = 'light'
  }
}

// Data for your projects
const projects = ref([
  {
    title: 'CampusBite',
    description: 'A university cafeteria pre-order system built with Vue.js and Express.js.',
    tech: ['On Process'], 
    // 'Vue.js', 'Express', 'Tailwind'
    link: '#',
    image: '/campusbite.jpg' 
  },
  {
    title: 'Personal Portfolio',
    description: 'Responsive portfolio website showcasing my skills as a final year CS student.',
    tech: ['Vue.js', 'Vite', 'Tailwind'],
    link: '#',
    image: '/portfolio.jpg' 
  },
  {
    title: 'IntelliGency Branding',
    description: 'Branding and design project for IntelliGency Solutions using Canva and Figma.',
    tech: ['Figma', 'Illustrator', 'UI/UX'],
    link: 'https://www.intelligencysolutions.com/',
    image: '/intelligency.jpg' 
  },
  {
    title: 'Parlour Management System',
    description: 'A desktop application for managing a beauty parlour, built with Java Swing and MySQL.',
    tech: ['java', 'sql', 'javaswing'],
    link: 'https://github.com/theniyazkhan/parlourmanagementsysyem',
    image: '/parlour.jpg' 
  },
  {
    title: 'HealthBridge',
    description: 'One-stop health information portal built with PHP and MySQL, designed to provide users with reliable health resources and tools.',
    tech: ['HTML5', 'CSS3', 'JavaScript', 'PHP', 'MySQL'],
    link: 'https://github.com/theniyazkhan/HealthBridge',
    image: '/healthbridge.jpg' 
  },
  {
    title: 'Fluffy Bird',
    description: 'Simple 2D game developed in Java using Swing, where players control a bird navigating through obstacles.',
    tech: ['java', 'swing'],
    link: 'https://github.com/theniyazkhan/birdgame',
    image: '/fluffybird.jpg' 
  }
])

// Technical Expertise Categories (Balanced for a 3-column layout)
const expertise = ref([
  {
    category: 'Programming & Data',
    skills: ['C/C++', 'Java', 'Python', 'SQL']
  },
  {
    category: 'Full-Stack Web',
    skills: ['HTML & CSS', 'Vue.js', 'React.js', 'Node.js', 'Express', 'PHP']
  },
  {
    category: 'UI/UX & Design',
    skills: ['Figma', 'Adobe XD', 'Adobe Photoshop', 'Adobe Illustrator']
  }
])
</script>

<template>
  <div class="min-h-screen bg-slate-50 dark:bg-slate-950 text-slate-900 dark:text-slate-50 font-sans selection:bg-blue-200 dark:selection:bg-blue-900 transition-colors duration-300">
    
    <nav class="sticky top-0 z-50 bg-white/80 dark:bg-slate-950/80 backdrop-blur-md border-b border-slate-200 dark:border-slate-800 transition-colors duration-300 slide-down">
      <div class="max-w-6xl mx-auto px-6 h-16 flex items-center justify-between">
        <span class="text-xl font-bold bg-gradient-to-r from-blue-600 to-indigo-600 dark:from-blue-400 dark:to-indigo-400 bg-clip-text text-transparent hover:scale-105 transition-transform cursor-pointer">
          Niyaz Ahmad Khan
        </span>
        <div class="hidden md:flex items-center space-x-8 font-medium">
          <a href="#about" class="text-slate-600 dark:text-slate-300 hover:text-blue-600 dark:hover:text-blue-400 transition">About</a>
          <a href="#skills" class="text-slate-600 dark:text-slate-300 hover:text-blue-600 dark:hover:text-blue-400 transition">Skills</a>
          <a href="#projects" class="text-slate-600 dark:text-slate-300 hover:text-blue-600 dark:hover:text-blue-400 transition">Projects</a>
          <a href="mailto:ahmadkhanniyaz@gmail.com" class="bg-blue-600 dark:bg-blue-500 text-white px-5 py-2 rounded-full hover:bg-blue-700 dark:hover:bg-blue-600 hover:-translate-y-0.5 active:scale-95 transition-all shadow-lg shadow-blue-200 dark:shadow-blue-900/50">
            Hire Me
          </a>
          <button @click="toggleDarkMode" class="p-2.5 rounded-full bg-slate-100 dark:bg-slate-800 text-slate-600 dark:text-slate-300 hover:bg-slate-200 dark:hover:bg-slate-700 hover:rotate-12 active:scale-90 transition-all" aria-label="Toggle Dark Mode">
            <svg v-if="!isDark" xmlns="http://www.w3.org/2000/svg" class="h-5 w-5" fill="none" viewBox="0 0 24 24" stroke="currentColor">
              <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M20.354 15.354A9 9 0 018.646 3.646 9.003 9.003 0 0012 21a9.003 9.003 0 008.354-5.646z" />
            </svg>
            <svg v-else xmlns="http://www.w3.org/2000/svg" class="h-5 w-5" fill="none" viewBox="0 0 24 24" stroke="currentColor">
              <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M12 3v1m0 16v1m9-9h-1M4 12H3m15.364 6.364l-.707-.707M6.343 6.343l-.707-.707m12.728 0l-.707.707M6.343 17.657l-.707.707M16 12a4 4 0 11-8 0 4 4 0 018 0z" />
            </svg>
          </button>
        </div>
      </div>
    </nav>

    <header id="home" class="max-w-6xl mx-auto px-6 py-24 md:py-32 flex flex-col md:flex-row items-center justify-between gap-12 overflow-hidden">
      <div class="flex-1 text-center md:text-left">
        <div class="fade-in-up delay-100">
          <span class="inline-block px-4 py-1.5 mb-6 text-sm font-semibold tracking-wide text-blue-600 dark:text-blue-400 uppercase bg-blue-50 dark:bg-blue-900/30 rounded-full">
            Final Year CS & Engineering Student
          </span>
        </div>
        
        <h1 class="fade-in-up delay-200 text-5xl md:text-7xl font-extrabold tracking-tight mb-6 text-slate-900 dark:text-white">
          Hello, from <span class="text-blue-600 dark:text-blue-500">Niyaz</span>!
        </h1>
        
        <p class="fade-in-up delay-300 text-xl text-slate-600 dark:text-slate-400 leading-relaxed mb-8 max-w-2xl mx-auto md:mx-0">
          Currently focused on performance-driven web development. Through deep user research and data analysis, 
          I uncover exactly why website visitors aren't converting into purchases—and engineer the technical solutions to 
          turn that traffic into revenue.
        </p>
        
        <div class="fade-in-up delay-400 flex flex-wrap justify-center md:justify-start gap-4">
          <a href="#projects" class="px-8 py-3 bg-slate-900 dark:bg-white text-white dark:text-slate-900 rounded-xl font-semibold hover:bg-slate-800 dark:hover:bg-slate-200 hover:-translate-y-1 active:scale-95 transition-all shadow-lg hover:shadow-xl">
            View My Work
          </a>
          <a href="#skills" class="px-8 py-3 bg-white dark:bg-slate-900 border border-slate-200 dark:border-slate-700 text-slate-900 dark:text-white rounded-xl font-semibold hover:border-blue-600 dark:hover:border-blue-500 hover:text-blue-600 dark:hover:text-blue-400 hover:-translate-y-1 active:scale-95 transition-all shadow-sm hover:shadow-md">
            Technical Skills
          </a>
        </div>
      </div>

      <div class="flex-1 flex justify-center md:justify-end fade-in-up delay-500">
        <img src="/me.jpg" alt="Niyaz" class="w-64 h-64 md:w-80 md:h-80 rounded-full border-4 border-blue-600 dark:border-blue-500 shadow-2xl object-cover bg-slate-200 dark:bg-slate-800 hover:scale-105 transition-transform duration-500">
      </div>
    </header>
    
    <section id="about" class="bg-slate-100/50 dark:bg-slate-900/50 py-24 border-y border-slate-200 dark:border-slate-800 transition-colors duration-300">
      <div class="max-w-6xl mx-auto px-6 flex flex-col md:flex-row gap-16 items-center">
        <div class="md:w-1/3 fade-in-up">
          <h2 class="text-4xl font-bold text-slate-900 dark:text-white mb-6">About Me</h2>
          <div class="h-1.5 w-20 bg-blue-600 dark:bg-blue-500 rounded-full mb-8"></div>
          <div class="pl-6 border-l-4 border-blue-200 dark:border-blue-900/50">
            <p class="text-xl text-slate-600 dark:text-slate-400 italic leading-relaxed">
              "An enthusiastic and adaptable problem-solver bridging the gap between web development, digital visibility, and visual design."
            </p>
          </div>
        </div>
        
        <div class="md:w-2/3 space-y-6 text-lg text-slate-600 dark:text-slate-400 fade-in-up delay-200">
          <p>
            I am a final-year Computer Science and Engineering student at <strong class="text-slate-900 dark:text-slate-200">Metropolitan University, Sylhet</strong>, graduating in 2026. I am a self-motivated and responsible team player, possessing a strong drive to build reliable digital solutions and adapt to challenging environments.
          </p>
          <p>
            Professionally, I wear multiple hats. Currently, I work as a <strong class="text-slate-900 dark:text-slate-200">GTM Engineer at IntelliGency Solutions</strong>. This unique combination allows me to not only build functional, responsive web applications—like my recent full-stack project, CampusBite—but also ensure they are optimized for search engines and digital marketing success.
          </p>
          <p>
            Before diving deeply into code and GTM, I honed my creative skills as a Graphic Designer for the Islamic Online Madrasah (IOM) and as a Senior Visual Designer. Whether I am competing under pressure—such as winning as the <strong class="text-slate-900 dark:text-slate-200">Champion of MU CSE FEST 2024</strong> (Design Segment)—or collaborating on a team, I leverage my diverse background in tech, marketing, and design to deliver well-rounded digital experiences.
          </p>
        </div>
      </div>
    </section>

   <section id="skills" class="bg-white dark:bg-slate-950 py-24 border-y border-slate-200 dark:border-slate-800 transition-colors duration-300">
      <div class="max-w-6xl mx-auto px-6">
        <h2 class="fade-in-up text-3xl md:text-4xl font-bold mb-16 text-center text-slate-900 dark:text-white">
          Technical Expertise
        </h2>
        
        <div class="grid grid-cols-1 md:grid-cols-3 gap-8">
          <div v-for="(group, index) in expertise" :key="group.category" 
               class="fade-in-up p-8 bg-slate-50 dark:bg-slate-900/50 rounded-3xl border border-slate-200 dark:border-slate-800 hover:shadow-xl hover:shadow-blue-100 dark:hover:shadow-blue-900/10 hover:-translate-y-1 transition-all duration-300 flex flex-col"
               :style="{ animationDelay: `${index * 150}ms` }">
            
            <h3 class="text-sm font-bold text-blue-600 dark:text-blue-500 tracking-wider uppercase mb-6">
              {{ group.category }}
            </h3>
            
            <div class="flex flex-wrap gap-3">
              <span v-for="skill in group.skills" :key="skill" 
                    class="px-4 py-2 bg-white dark:bg-slate-800/80 text-slate-700 dark:text-slate-300 text-sm font-medium rounded-xl border border-slate-200 dark:border-slate-700/50 hover:border-blue-400 dark:hover:border-blue-500 hover:text-blue-600 dark:hover:text-blue-400 transition-colors cursor-default shadow-sm dark:shadow-none">
                {{ skill }}
              </span>
            </div>
          </div>
        </div>
      </div>
    </section>

    <section id="projects" class="max-w-6xl mx-auto px-6 py-24">
      <div class="flex items-end justify-between mb-16">
        <div class="fade-in-up">
          <h2 class="text-4xl font-bold mb-4 text-slate-900 dark:text-white">Significant Works</h2>
          <p class="text-slate-600 dark:text-slate-400">A collection of academic and personal work.</p>
        </div>
      </div>
      
      <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-8">
        <div v-for="(project, index) in projects" :key="project.title" 
             class="fade-in-up group bg-white dark:bg-slate-900 rounded-3xl border border-slate-200 dark:border-slate-800 overflow-hidden hover:shadow-2xl hover:shadow-blue-100 dark:hover:shadow-blue-900/20 hover:-translate-y-3 transition-all duration-500 flex flex-col"
             :style="{ animationDelay: `${index * 150}ms` }">
          
          <div class="aspect-video bg-slate-100 dark:bg-slate-800 flex items-center justify-center relative overflow-hidden">
             
             <img v-if="project.image" :src="project.image" :alt="project.title" class="w-full h-full object-cover group-hover:scale-110 transition-transform duration-700 z-0">
             
             <div class="absolute inset-0 bg-gradient-to-br from-blue-400 to-indigo-600 opacity-10 dark:opacity-40 group-hover:opacity-30 dark:group-hover:opacity-60 transition-all duration-700 z-10 mix-blend-multiply dark:mix-blend-color-burn"></div>
             
             <span v-if="!project.image" class="text-slate-400 dark:text-slate-500 font-medium z-20 group-hover:scale-110 transition-transform duration-500">Project Preview</span>
          
          </div>
          <div class="p-8 flex flex-col flex-1">
            <h3 class="text-2xl font-bold mb-3 text-slate-900 dark:text-white group-hover:text-blue-600 dark:group-hover:text-blue-400 transition-colors">{{ project.title }}</h3>
            <p class="text-slate-600 dark:text-slate-400 mb-6 line-clamp-2 leading-relaxed flex-1">
              {{ project.description }}
            </p>
            <div class="flex flex-wrap gap-2 mb-6">
              <span v-for="t in project.tech" :key="t" 
                    class="px-3 py-1.5 bg-slate-100 dark:bg-slate-800 text-slate-600 dark:text-slate-300 text-xs font-bold rounded-full uppercase tracking-wider group-hover:bg-blue-50 dark:group-hover:bg-blue-900/30 group-hover:text-blue-600 dark:group-hover:text-blue-400 transition-colors">
                {{ t }}
              </span>
            </div>
            <a :href="project.link" class="inline-flex items-center font-bold text-blue-600 dark:text-blue-400 hover:gap-3 transition-all w-max">
              View Project <span class="ml-1">→</span>
            </a>
          </div>
        </div>
      </div>
    </section>

    <footer class="bg-slate-900 dark:bg-black text-white py-16 border-t border-slate-800 dark:border-slate-900 transition-colors duration-300">
      <div class="max-w-6xl mx-auto px-6 text-center">
        <h2 class="text-3xl font-bold mb-8 italic">Interested in collaborating?</h2>
        <p class="text-slate-400 mb-12 max-w-xl mx-auto">
          I'm currently looking for new opportunities in web development and research projects.
        </p>
        
        <div class="flex justify-center space-x-6 text-slate-400">
          <a href="https://github.com/theniyazkhan" target="_blank" rel="noopener noreferrer" class="hover:text-white hover:scale-110 hover:-translate-y-1 transition-all duration-300" aria-label="GitHub">
            <svg class="w-7 h-7" fill="currentColor" viewBox="0 0 24 24" aria-hidden="true">
              <path fill-rule="evenodd" d="M12 2C6.477 2 2 6.484 2 12.017c0 4.425 2.865 8.18 6.839 9.504.5.092.682-.217.682-.483 0-.237-.008-.868-.013-1.703-2.782.605-3.369-1.343-3.369-1.343-.454-1.158-1.11-1.466-1.11-1.466-.908-.62.069-.608.069-.608 1.003.07 1.531 1.032 1.531 1.032.892 1.53 2.341 1.088 2.91.832.092-.647.35-1.088.636-1.338-2.22-.253-4.555-1.113-4.555-4.951 0-1.093.39-1.988 1.029-2.688-.103-.253-.446-1.272.098-2.65 0 0 .84-.27 2.75 1.026A9.564 9.564 0 0112 6.844c.85.004 1.705.115 2.504.337 1.909-1.296 2.747-1.027 2.747-1.027.546 1.379.202 2.398.1 2.651.64.7 1.028 1.595 1.028 2.688 0 3.848-2.339 4.695-4.566 4.943.359.309.678.92.678 1.855 0 1.338-.012 2.419-.012 2.747 0 .268.18.58.688.482A10.019 10.019 0 0022 12.017C22 6.484 17.522 2 12 2z" clip-rule="evenodd" />
            </svg>
          </a>
          <a href="https://www.linkedin.com/in/theniyazkhan/" target="_blank" rel="noopener noreferrer" class="hover:text-blue-400 hover:scale-110 hover:-translate-y-1 transition-all duration-300" aria-label="LinkedIn">
            <svg class="w-7 h-7" fill="currentColor" viewBox="0 0 24 24" aria-hidden="true">
              <path fill-rule="evenodd" d="M19 0h-14c-2.761 0-5 2.239-5 5v14c0 2.761 2.239 5 5 5h14c2.762 0 5-2.239 5-5v-14c0-2.761-2.238-5-5-5zm-11 19h-3v-11h3v11zm-1.5-12.268c-.966 0-1.75-.79-1.75-1.764s.784-1.764 1.75-1.764 1.75.79 1.75 1.764-.783 1.764-1.75 1.764zm13.5 12.268h-3v-5.604c0-3.368-4-3.113-4 0v5.604h-3v-11h3v1.765c1.396-2.586 7-2.777 7 2.476v6.759z" clip-rule="evenodd" />
            </svg>
          </a>
          <a href="https://www.behance.net/theniyazkhan" target="_blank" rel="noopener noreferrer" class="hover:text-blue-500 hover:scale-110 hover:-translate-y-1 transition-all duration-300" aria-label="Behance">
            <svg class="w-7 h-7" fill="currentColor" viewBox="0 0 24 24" aria-hidden="true">
              <path fill-rule="evenodd" d="M22 7h-7v-2h7v2zm1.726 10c-.442 1.297-2.029 3-5.101 3-3.074 0-5.564-1.729-5.564-5.675 0-3.91 2.325-5.92 5.466-5.92 3.082 0 4.964 1.782 5.375 4.8h-6.896c.162 1.905 1.503 2.923 3.328 2.923 1.343 0 2.47-.69 2.94-1.614h4.452zm-3.018-4.22c-.173-1.077-1.129-1.921-2.486-1.921-1.352 0-2.378.808-2.583 1.921h5.069zm-10.741 4.22h-9.967v-14h9.118c2.812 0 5.097 1.348 5.097 4.22 0 1.636-.957 2.898-2.316 3.486 1.783.565 2.84 1.933 2.84 3.901 0 3.024-2.531 4.393-4.772 4.393zm-5.553-9.529h4.301c1.393 0 2.215-.71 2.215-1.897 0-1.15-.815-1.776-2.128-1.776h-4.388v3.673zm0 5.759h4.743c1.55 0 2.502-.8 2.502-2.155 0-1.393-.952-2.115-2.508-2.115h-4.737v4.27z" clip-rule="evenodd" />
            </svg>
          </a>
        </div>
        <div class="mt-16 pt-8 border-t border-slate-800 text-sm text-slate-500">
          © 2026 Niyaz. Built with Vue.js & Tailwind CSS.
        </div>
      </div>
    </footer>
  </div>
</template>

<style scoped>
@keyframes fadeInUp {
  from { opacity: 0; transform: translateY(30px); }
  to { opacity: 1; transform: translateY(0); }
}

@keyframes slideDown {
  from { opacity: 0; transform: translateY(-100%); }
  to { opacity: 1; transform: translateY(0); }
}

.fade-in-up {
  opacity: 0;
  animation-name: fadeInUp;
  animation-duration: 0.8s;
  animation-timing-function: cubic-bezier(0.16, 1, 0.3, 1);
  animation-fill-mode: forwards;
}

.slide-down {
  animation-name: slideDown;
  animation-duration: 0.6s;
  animation-timing-function: cubic-bezier(0.16, 1, 0.3, 1);
  animation-fill-mode: forwards;
}

.delay-100 { animation-delay: 100ms !important; }
.delay-200 { animation-delay: 200ms !important; }
.delay-300 { animation-delay: 300ms !important; }
.delay-400 { animation-delay: 400ms !important; }
.delay-500 { animation-delay: 500ms !important; }
</style>