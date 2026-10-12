<script setup>
import { ref, reactive, onMounted, onUnmounted } from "vue";

const menuOpen = ref(false);

const projects = [
  {
    number: "01",
    name: "JomBarter",
    category: "WEB APPLICATION",
    description:
      "A peer-to-peer barter platform designed to help people exchange items and discover value beyond money.",
    tags: ["Vue.js", "NestJS", "Prisma", "SQL"],
    status: "IN DEVELOPMENT",
    symbol: "↗",
    color: "pink",
    url: "", // Add your deployed project URL later
    repoUrl: "https://github.com/ElisaesterYsn/JomBarter",
    screenshots: [
      {
        src: "/images/JomBarter1.png",
        alt: "JomBarter home page showing featured barter listings",
      },
      {
        src: "/images/JomBarter2.png",
        alt: "JomBarter item detail view with exchange options",
      },
      {
        src: "/images/JomBarter3.png",
        alt: "JomBarter user profile and active barter history",
      },
      {
        src: "/images/JomBarter4.png",
        alt: "JomBarter search and filter interface",
      },
    ],
  },
  {
    number: "02",
    name: "TARO AI",
    category: "ARTIFICIAL INTELLIGENCE",
    description:
      "A conversational AI assistant exploring local AI models, memory, and more natural digital interactions.",
    tags: ["Vue.js", "FastAPI", "Python", "Ollama"],
    status: "IN DEVELOPMENT",
    symbol: "✳",
    color: "plum",
    url: "", // Add your deployed project URL later
    repoUrl: "https://github.com/ElisaesterYsn/TARO-AI-ChatBot",
    screenshots: [
      {
        src: "/images/Taro1.png",
        alt: "TARO AI chat interface with conversation history",
      },
      {
        src: "/images/Taro2.png",
        alt: "TARO AI settings panel showing model configuration",
      },
      {
        src: "/images/Taro3.png",
        alt: "TARO AI responding to natural language queries",
      },
    ],
  },
];

// Track active screenshot index for each project
const activeScreenshot = reactive({});
projects.forEach((project) => {
  activeScreenshot[project.number] = 0;
});

const setActiveScreenshot = (projectNumber, index) => {
  activeScreenshot[projectNumber] = index;
};

const closeMenu = () => {
  menuOpen.value = false;
};

// Scroll reveal animation using IntersectionObserver
let observer = null;

onMounted(() => {
  // Create observer for scroll reveal animations (works in both directions)
  observer = new IntersectionObserver(
    (entries) => {
      entries.forEach((entry) => {
        if (entry.isIntersecting) {
          // Add class when entering viewport
          entry.target.classList.add("animate-in");
        } else {
          // Remove class when leaving viewport to allow re-animation
          entry.target.classList.remove("animate-in");
        }
      });
    },
    {
      threshold: 0.1,
      rootMargin: "0px 0px -50px 0px",
    },
  );

  // Observe sections for scroll reveal
  const sections = document.querySelectorAll(".animate-on-scroll");
  sections.forEach((section) => observer.observe(section));
});

onUnmounted(() => {
  // Clean up observer
  if (observer) {
    observer.disconnect();
  }
});
</script>

<template>
  <div class="min-h-screen bg-[#0d0b0e] text-[#f9edf3]">
    <!-- Navigation -->
    <header
      class="sticky top-0 z-50 border-b border-white/[0.06] bg-[#0d0b0e]/90 backdrop-blur-xl"
    >
      <nav
        class="relative mx-auto flex max-w-6xl items-center justify-between px-6 py-5 lg:px-10"
        aria-label="Main navigation"
      >
        <a
          href="#home"
          class="text-lg font-semibold tracking-tight"
          @click="closeMenu"
        >
          Eli<span class="text-[#f4b8d0]"></span>
          <span class="font-normal text-[#b8aab4]">eSt</span>
          <span class="font-normal text-[#f4b8d0]">udio</span>
        </a>

        <button
          class="rounded-lg border border-white/10 px-3 py-2 text-sm text-[#f9edf3] md:hidden"
          :aria-expanded="menuOpen"
          aria-controls="mobile-menu"
          aria-label="Toggle navigation"
          @click="menuOpen = !menuOpen"
        >
          {{ menuOpen ? "Close" : "Menu" }}
        </button>

        <div class="hidden items-center gap-8 md:flex">
          <a href="#about" class="nav-link">About</a>
          <a href="#projects" class="nav-link">Projects</a>
          <a href="#contact" class="nav-link">Contact</a>
          <a
            href="#projects"
            class="rounded-full bg-[#f4b8d0] px-5 py-2.5 text-sm font-medium text-[#24131c] transition hover:bg-[#f9dce8]"
          >
            Explore my work ↗
          </a>
        </div>

        <div
          v-if="menuOpen"
          id="mobile-menu"
          class="absolute left-0 right-0 top-full flex flex-col gap-5 border-b border-white/10 bg-[#0d0b0e] px-6 py-6 md:hidden"
        >
          <a href="#about" class="nav-link" @click="closeMenu">About</a>
          <a href="#projects" class="nav-link" @click="closeMenu">Projects</a>
          <a href="#contact" class="nav-link" @click="closeMenu">Contact</a>
        </div>
      </nav>
    </header>

    <main>
      <!-- Hero -->
      <section
        id="home"
        class="relative mx-auto flex min-h-[78vh] max-w-6xl items-center overflow-hidden px-6 py-24 lg:px-10 lg:py-32"
      >
        <div
          class="pointer-events-none absolute -right-32 top-16 h-80 w-80 rounded-full bg-[#d77da5]/[0.08] blur-[100px]"
        ></div>

        <div class="relative max-w-3xl">
          <div
            class="mb-8 inline-flex items-center gap-3 rounded-full border border-[#493442] bg-[#171218] px-4 py-2 hero-badge"
          >
            <span class="h-2 w-2 rounded-full bg-[#f4b8d0]"></span>
            <span class="text-xs tracking-wide text-[#e5cbd8]">
              Full Stack Developer · Sabah, Malaysia
            </span>
          </div>

          <p
            class="mb-5 text-sm font-medium uppercase tracking-[0.3em] text-[#f4b8d0] sm:tracking-[0.3em] tracking-[0.15em] hero-tagline"
          >
            Welcome to my little corner of the internet
          </p>

          <h1
            class="text-5xl font-semibold leading-[1.08] tracking-[-0.055em] sm:text-7xl lg:text-8xl break-words hero-heading"
          >
            Code.
            <span class="text-[#f4b8d0]">Create.</span>
            <span class="block">Experiment.</span>
          </h1>

          <p
            class="mt-8 max-w-xl text-base leading-8 text-[#b8aab4] sm:text-lg hero-description"
          >
            I'm a developer who loves turning ideas into digital experiences.
            Here, I build software, explore AI, and experiment with things that
            make the digital world a little more interesting.
          </p>

          <div class="mt-10 flex flex-wrap items-center gap-4 hero-buttons">
            <a
              href="#projects"
              class="rounded-full bg-[#f4b8d0] px-7 py-3.5 text-sm font-semibold text-[#24131c] transition hover:-translate-y-0.5 hover:bg-[#f9dce8]"
            >
              Explore my projects ↗
            </a>
            <a
              href="#about"
              class="rounded-full border border-[#493442] px-7 py-3.5 text-sm text-[#f9edf3] transition hover:border-[#f4b8d0]/60 hover:bg-[#171218]"
            >
              A little about me
            </a>
          </div>

          <div
            class="mt-16 flex items-center gap-3 text-xs tracking-wide text-[#8f818b] overflow-hidden"
          >
            <span class="h-px w-10 bg-[#f4b8d0]/50 flex-shrink-0"></span>
            <span class="break-words"
              >BUILDING WITH CURIOSITY, ONE PROJECT AT A TIME</span
            >
          </div>
        </div>
      </section>

      <!-- About -->
      <section
        id="about"
        class="border-t border-white/[0.06] bg-[#110e12] px-6 py-24 lg:px-10 lg:py-28 animate-on-scroll"
      >
        <div
          class="mx-auto grid max-w-6xl gap-12 md:grid-cols-[0.8fr_1.2fr] md:gap-20"
        >
          <div>
            <p class="section-label">01 / A LITTLE INTRODUCTION</p>
            <h2 class="mt-5 text-3xl font-semibold tracking-tight sm:text-4xl">
              The person behind
              <span class="text-[#f4b8d0]">the pixels.</span>
            </h2>
          </div>

          <div class="space-y-5 text-base leading-8 text-[#b8aab4]">
            <p>
              Hey, I'm Eli — a developer interested in building useful
              applications, exploring emerging technologies, and bringing ideas
              to life through code.
            </p>
            <p>
              My work spans web development, AI experiments, and tools that
              solve everyday problems. I enjoy the process of learning,
              building, breaking things, and making them better.
            </p>
            <p>
              <span class="text-[#f9edf3]">ElieStudio Studio</span> is where I
              document that journey and share the things I'm creating along the
              way.
            </p>

            <div class="flex flex-wrap gap-2 pt-3">
              <span
                v-for="skill in [
                  'Frontend Development',
                  'Backend Development',
                  'AI Experiments',
                  'Product Building',
                ]"
                :key="skill"
                class="rounded-full border border-[#493442] px-4 py-2 text-xs text-[#e5cbd8]"
              >
                {{ skill }}
              </span>
            </div>
          </div>
        </div>
      </section>

      <!-- Projects -->
      <section
        id="projects"
        class="mx-auto max-w-6xl px-6 py-24 lg:px-10 lg:py-28 animate-on-scroll"
      >
        <div
          class="flex flex-col justify-between gap-5 sm:flex-row sm:items-end"
        >
          <div>
            <p class="section-label">02 / SELECTED WORK</p>
            <h2 class="mt-5 text-3xl font-semibold tracking-tight sm:text-4xl">
              Things I'm
              <span class="text-[#f4b8d0]">building.</span>
            </h2>
          </div>
          <p class="max-w-sm text-sm leading-7 text-[#b8aab4]">
            A collection of products, experiments, and ideas in progress. More
            projects will find their way here.
          </p>
        </div>

        <div class="mt-12 grid gap-5 md:grid-cols-2">
          <article
            v-for="project in projects"
            :key="project.number"
            class="group flex flex-col rounded-2xl border border-[#352630] bg-[#171218] p-7 transition-all duration-300 hover:-translate-y-2 hover:shadow-lg hover:shadow-[#f4b8d0]/10 hover:border-[#f4b8d0]/40 sm:p-9"
          >
            <div class="flex items-start justify-between gap-4">
              <span class="text-xs tracking-[0.2em] text-[#8f818b]">
                PROJECT {{ project.number }}
              </span>
              <span
                :class="
                  project.color === 'pink' ? 'text-[#f4b8d0]' : 'text-[#c6a5d7]'
                "
                class="text-3xl transition-transform group-hover:rotate-12"
                aria-hidden="true"
              >
                {{ project.symbol }}
              </span>
            </div>

            <!-- Screenshot Gallery -->
            <div v-if="project.screenshots" class="mt-6">
              <!-- Main Screenshot Display -->
              <div
                class="overflow-hidden rounded-xl border border-[#352630] bg-[#0d0b0e]"
              >
                <img
                  :src="
                    project.screenshots[activeScreenshot[project.number]].src
                  "
                  :alt="
                    project.screenshots[activeScreenshot[project.number]].alt
                  "
                  class="w-full h-48 object-cover transition-opacity duration-300"
                  loading="lazy"
                />
              </div>

              <!-- Thumbnail Navigation -->
              <div class="mt-3 flex gap-2 overflow-x-auto pb-2">
                <button
                  v-for="(screenshot, index) in project.screenshots"
                  :key="index"
                  @click="setActiveScreenshot(project.number, index)"
                  :class="[
                    'flex-shrink-0 overflow-hidden rounded-lg border-2 transition-all duration-200',
                    activeScreenshot[project.number] === index
                      ? 'border-[#f4b8d0] ring-2 ring-[#f4b8d0]/20'
                      : 'border-[#352630] hover:border-[#f4b8d0]/60',
                  ]"
                  :aria-label="`View screenshot ${index + 1} of ${project.name}`"
                >
                  <img
                    :src="screenshot.src"
                    :alt="screenshot.alt"
                    class="w-16 h-12 object-cover"
                    loading="lazy"
                  />
                </button>
              </div>
            </div>

            <p
              class="mt-6 text-[10px] font-medium tracking-[0.22em] text-[#b8aab4]"
            >
              {{ project.category }}
            </p>

            <h3 class="mt-3 text-3xl font-semibold tracking-tight">
              {{ project.name }}
            </h3>

            <p class="mt-4 max-w-md text-sm leading-7 text-[#b8aab4]">
              {{ project.description }}
            </p>

            <div class="mt-6 flex flex-wrap gap-2">
              <span
                v-for="tag in project.tags"
                :key="tag"
                class="rounded-md border border-white/[0.08] px-2.5 py-1.5 text-[11px] text-[#d5c6cf]"
              >
                {{ tag }}
              </span>
            </div>

            <div
              class="mt-auto flex items-center justify-between gap-3 pt-8 flex-wrap"
            >
              <span class="text-[10px] tracking-[0.16em] text-[#f4b8d0]">
                {{ project.status }}
              </span>
              <a
                v-if="project.url"
                :href="project.url"
                target="_blank"
                rel="noopener noreferrer"
                class="text-sm text-[#f4b8d0] transition hover:text-[#f9dce8]"
              >
                View project ↗
              </a>
              <a
                v-else-if="project.repoUrl"
                :href="project.repoUrl"
                target="_blank"
                rel="noopener noreferrer"
                class="text-sm text-[#f4b8d0] transition hover:text-[#f9dce8]"
              >
                View source ↗
              </a>
              <span v-else class="text-xs text-[#8f818b]">
                More details soon
              </span>
            </div>
          </article>
        </div>

        <p class="mt-8 text-center text-xs leading-6 text-[#8f818b]">
          These projects are works in progress. Features and availability may
          change.
        </p>
      </section>

      <!-- Contact -->
      <section
        id="contact"
        class="border-t border-white/[0.06] bg-[#110e12] px-6 py-24 lg:px-10 lg:py-28 animate-on-scroll"
      >
        <div class="mx-auto max-w-3xl text-center">
          <p class="section-label">03 / LET'S CONNECT</p>

          <h2
            class="mt-6 text-4xl font-semibold tracking-tight sm:text-6xl break-words"
          >
            Have an idea?
            <span class="block mt-2 text-[#f4b8d0]">Let's make it real.</span>
          </h2>

          <p class="mx-auto mt-6 max-w-lg text-base leading-8 text-[#b8aab4]">
            Interested in my work, have a project in mind, or just want to talk
            about technology? I'd love to hear from you.
          </p>

          <!-- Email Button -->
          <a
            href="mailto:elisaesteryasun18@gmail.com"
            class="mt-9 inline-flex items-center gap-2 rounded-full bg-[#f4b8d0] px-7 py-3.5 text-sm font-semibold text-[#24131c] transition hover:-translate-y-0.5 hover:bg-[#f9dce8] focus-visible:outline focus-visible:outline-2 focus-visible:outline-offset-2 focus-visible:outline-[#f4b8d0]"
          >
            <svg
              xmlns="http://www.w3.org/2000/svg"
              viewBox="0 0 24 24"
              fill="currentColor"
              class="w-5 h-5"
              aria-hidden="true"
            >
              <path
                d="M1.5 8.67v8.58a3 3 0 003 3h15a3 3 0 003-3V8.67l-8.928 5.493a3 3 0 01-3.144 0L1.5 8.67z"
              />
              <path
                d="M22.5 6.908V6.75a3 3 0 00-3-3h-15a3 3 0 00-3 3v.158l9.714 5.978a1.5 1.5 0 001.572 0L22.5 6.908z"
              />
            </svg>
            Email Me
          </a>

          <!-- Social Links -->
          <div class="mt-8 flex items-center justify-center gap-5">
            <a
              href="https://github.com/ElisaesterYsn"
              target="_blank"
              rel="noopener noreferrer"
              class="group inline-flex h-12 w-12 items-center justify-center rounded-full border border-[#493442] text-[#b8aab4] transition hover:border-[#f4b8d0] hover:bg-[#171218] hover:text-[#f4b8d0] focus-visible:outline focus-visible:outline-2 focus-visible:outline-offset-2 focus-visible:outline-[#f4b8d0]"
              aria-label="Visit my GitHub profile"
            >
              <svg
                xmlns="http://www.w3.org/2000/svg"
                viewBox="0 0 24 24"
                fill="currentColor"
                class="h-5 w-5"
                aria-hidden="true"
              >
                <path
                  d="M12 0c-6.626 0-12 5.373-12 12 0 5.302 3.438 9.8 8.207 11.387.599.111.793-.261.793-.577v-2.234c-3.338.726-4.033-1.416-4.033-1.416-.546-1.387-1.333-1.756-1.333-1.756-1.089-.745.083-.729.083-.729 1.205.084 1.839 1.237 1.839 1.237 1.07 1.834 2.807 1.304 3.492.997.107-.775.418-1.305.762-1.604-2.665-.305-5.467-1.334-5.467-5.931 0-1.311.469-2.381 1.236-3.221-.124-.303-.535-1.524.117-3.176 0 0 1.008-.322 3.301 1.23.957-.266 1.983-.399 3.003-.404 1.02.005 2.047.138 3.006.404 2.291-1.552 3.297-1.23 3.297-1.23.653 1.653.242 2.874.118 3.176.77.84 1.235 1.911 1.235 3.221 0 4.609-2.807 5.624-5.479 5.921.43.372.823 1.102.823 2.222v3.293c0 .319.192.694.801.576 4.765-1.589 8.199-6.086 8.199-11.386 0-6.627-5.373-12-12-12z"
                />
              </svg>
            </a>

            <a
              href="https://www.linkedin.com/in/elisaester-yasun-29294241b"
              target="_blank"
              rel="noopener noreferrer"
              class="group inline-flex h-12 w-12 items-center justify-center rounded-full border border-[#493442] text-[#b8aab4] transition hover:border-[#f4b8d0] hover:bg-[#171218] hover:text-[#f4b8d0] focus-visible:outline focus-visible:outline-2 focus-visible:outline-offset-2 focus-visible:outline-[#f4b8d0]"
              aria-label="Connect with me on LinkedIn"
            >
              <svg
                xmlns="http://www.w3.org/2000/svg"
                viewBox="0 0 24 24"
                fill="currentColor"
                class="h-5 w-5"
                aria-hidden="true"
              >
                <path
                  d="M20.447 20.452h-3.554v-5.569c0-1.328-.027-3.037-1.852-3.037-1.853 0-2.136 1.445-2.136 2.939v5.667H9.351V9h3.414v1.561h.046c.477-.9 1.637-1.85 3.37-1.85 3.601 0 4.267 2.37 4.267 5.455v6.286zM5.337 7.433c-1.144 0-2.063-.926-2.063-2.065 0-1.138.92-2.063 2.063-2.063 1.14 0 2.064.925 2.064 2.063 0 1.139-.925 2.065-2.064 2.065zm1.782 13.019H3.555V9h3.564v11.452zM22.225 0H1.771C.792 0 0 .774 0 1.729v20.542C0 23.227.792 24 1.771 24h20.451C23.2 24 24 23.227 24 22.271V1.729C24 .774 23.2 0 22.222 0h.003z"
                />
              </svg>
            </a>
          </div>
        </div>
      </section>
    </main>

    <!-- Footer -->
    <footer class="border-t border-white/[0.06] px-6 py-7 lg:px-10">
      <div
        class="mx-auto flex max-w-6xl flex-col gap-4 text-xs text-[#8f818b] sm:flex-row sm:items-center sm:justify-between"
      >
        <a
          href="#home"
          class="text-sm font-medium text-[#f9edf3] hover:text-[#f4b8d0] transition"
        >
          ElieStudio<span class="text-[#f4b8d0]">.</span> Studio
        </a>
        <p class="hidden sm:block">
          Designed with intention. Built with curiosity.
        </p>
        <div class="flex flex-wrap items-center gap-3 sm:gap-4">
          <a
            href="https://github.com/ElisaesterYsn"
            target="_blank"
            rel="noopener noreferrer"
            class="transition hover:text-[#f4b8d0]"
            aria-label="Visit my GitHub profile"
          >
            GitHub ↗
          </a>
          <p>© {{ new Date().getFullYear() }} ElieStudio Studio</p>
        </div>
      </div>
    </footer>
  </div>
</template>

<style scoped>
.nav-link {
  color: #b8aab4;
  font-size: 0.875rem;
  transition: color 180ms ease;
}

.nav-link:hover {
  color: #f4b8d0;
}

.section-label {
  color: #f4b8d0;
  font-size: 0.7rem;
  font-weight: 500;
  letter-spacing: 0.2em;
}

/* Custom scrollbar for thumbnail navigation */
.overflow-x-auto::-webkit-scrollbar {
  height: 6px;
}

.overflow-x-auto::-webkit-scrollbar-track {
  background: #171218;
  border-radius: 3px;
}

.overflow-x-auto::-webkit-scrollbar-thumb {
  background: #352630;
  border-radius: 3px;
}

.overflow-x-auto::-webkit-scrollbar-thumb:hover {
  background: #493442;
}

@media (prefers-reduced-motion: reduce) {
  *,
  *::before,
  *::after {
    scroll-behavior: auto !important;
    transition-duration: 0.01ms !important;
    animation-duration: 0.01ms !important;
  }
}
</style>
