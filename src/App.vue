<script setup>
import { ref } from "vue";

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
  },
];

const closeMenu = () => {
  menuOpen.value = false;
};
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
          Eli.Est<span class="text-[#f4b8d0]">.</span>
          <span class="font-normal text-[#b8aab4]">Studio</span>
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
            class="mb-8 inline-flex items-center gap-3 rounded-full border border-[#493442] bg-[#171218] px-4 py-2"
          >
            <span class="h-2 w-2 rounded-full bg-[#f4b8d0]"></span>
            <span class="text-xs tracking-wide text-[#e5cbd8]">
              Full Stack Developer · Sabah, Malaysia
            </span>
          </div>

          <p
            class="mb-5 text-sm font-medium uppercase tracking-[0.3em] text-[#f4b8d0] sm:tracking-[0.3em] tracking-[0.15em]"
          >
            Welcome to my little corner of the internet
          </p>

          <h1
            class="text-5xl font-semibold leading-[1.08] tracking-[-0.055em] sm:text-7xl lg:text-8xl break-words"
          >
            Code.
            <span class="text-[#f4b8d0]">Create.</span>
            <span class="block">Experiment.</span>
          </h1>

          <p
            class="mt-8 max-w-xl text-base leading-8 text-[#b8aab4] sm:text-lg"
          >
            I'm a developer who loves turning ideas into digital experiences.
            Here, I build software, explore AI, and experiment with things that
            make the digital world a little more interesting.
          </p>

          <div class="mt-10 flex flex-wrap items-center gap-4">
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
        class="border-t border-white/[0.06] bg-[#110e12] px-6 py-24 lg:px-10 lg:py-28"
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
              <span class="text-[#f9edf3]">Eli.Est. Studio</span> is where I
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
        class="mx-auto max-w-6xl px-6 py-24 lg:px-10 lg:py-28"
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
            class="group flex min-h-[360px] flex-col rounded-2xl border border-[#352630] bg-[#171218] p-7 transition duration-300 hover:-translate-y-1 hover:border-[#f4b8d0]/40 sm:p-9"
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

            <p
              class="mt-10 text-[10px] font-medium tracking-[0.22em] text-[#b8aab4]"
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
        class="border-t border-white/[0.06] bg-[#110e12] px-6 py-24 lg:px-10 lg:py-28"
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

          <!-- Replace this placeholder with your real email -->
          <a
            href="mailto:elisaesteryasun18@gmail.com"
            class="mt-9 inline-flex rounded-full bg-[#f4b8d0] px-7 py-3.5 text-sm font-semibold text-[#24131c] transition hover:-translate-y-0.5 hover:bg-[#f9dce8]"
          >
            Say hello ↗
          </a>
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
          Eli.Est<span class="text-[#f4b8d0]">.</span> Studio
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
          <p>© {{ new Date().getFullYear() }} Eli.Est. Studio</p>
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
