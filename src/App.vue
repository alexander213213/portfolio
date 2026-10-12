<template>
  <div class="page">
    <header class="site-header">
      <div class="brand">
        <a href="#top" class="avatar-link" aria-label="Home">
          <img src="/profile.jpg" alt="Alexander Gracilla" class="avatar" />
        </a>
        <div>
          <a href="#top" class="site-name">Alexander Gracilla</a>
          <nav class="desktop-nav" aria-label="Sections">
            <a href="#project">Project</a>
            <a href="#stack">Stack</a>
            <a href="#experience">Experience</a>
            <a href="#contact">Contact</a>
          </nav>
        </div>
      </div>
      <div class="header-actions">
        <button class="theme-toggle" type="button" @click="toggleTheme" :aria-label="theme === 'light' ? 'Switch to dark mode' : 'Switch to light mode'">
          {{ theme === 'light' ? 'Dark' : 'Light' }}
        </button>
        <button class="menu-btn" type="button" @click="menuOpen = !menuOpen" aria-label="Toggle menu">
          <svg v-if="!menuOpen" class="menu-icon" fill="currentColor" viewBox="0 0 20 20"><path d="M0 3h20v2H0V3zm0 6h20v2H0V9zm0 6h20v2H0v-2z"/></svg>
          <svg v-else class="menu-icon" fill="currentColor" viewBox="0 0 20 20"><path d="M10 8.586L2.929 1.515 1.515 2.929 8.586 10l-7.071 7.071 1.414 1.414L10 11.414l7.071 7.071 1.414-1.414L11.414 10l7.071-7.071-1.414-1.414L10 8.586z"/></svg>
        </button>
      </div>
    </header>

    <nav v-if="menuOpen" class="mobile-nav" aria-label="Sections mobile">
      <a href="#project" @click="menuOpen = false">Project</a>
      <a href="#stack" @click="menuOpen = false">Stack</a>
      <a href="#experience" @click="menuOpen = false">Experience</a>
      <a href="#contact" @click="menuOpen = false">Contact</a>
    </nav>

    <main id="top" class="content">
      <section class="block">
        <h1>Who the hell am I?</h1>
        <p>
          I'm <strong>Alexander Gracilla</strong>, a full-stack developer based in the
          Philippines (GMT+8), focused on backend architecture and predictable application workflows.
        </p>
        <p>
          I build reliable web applications with
          <strong>TypeScript, Node.js, PostgreSQL</strong>, and modern frontend frameworks like
          <strong>Vue 3</strong>. I care about data integrity, guarded state transitions, and APIs
          that behave the way you'd expect.
        </p>
        <p>
          Recently I built a <a href="#project"><strong>Task Marketplace platform</strong></a> —
          post tasks, submit proposals, assign workers, and leave reviews. It's the project below.
        </p>
        <p>
          I'm open to remote junior backend and full-stack roles worldwide. The fastest way to reach
          me is <a href="mailto:alexandergracilla@gmail.com"><strong>email</strong></a>, and all of
          my code lives on <a href="https://github.com/alexander213213" target="_blank" rel="noreferrer"><strong>GitHub</strong></a>.
        </p>
      </section>

      <section id="project" class="block">
        <h1>Featured project</h1>
        <p>
          <strong>Task Marketplace Platform</strong> — a simplified service marketplace where users
          post tasks, workers submit proposals, owners assign a worker, and owners review the work
          when it's done.
        </p>
        <p>
          The interesting part isn't the UI, it's the rules underneath: strictly guarded task states
          (<code>OPEN → ASSIGNED → SUBMITTED → COMPLETED</code>), transactional rating updates,
          JWT auth with refresh rotation, Zod validation, and cursor-based pagination.
        </p>
        <ul class="plain-list">
          <li><strong>Live frontend:</strong> <a href="https://tasker-demo.vercel.app" target="_blank" rel="noreferrer">tasker-demo.vercel.app</a></li>
          <li><strong>Backend API:</strong> <a href="https://github.com/alexander213213/task-api" target="_blank" rel="noreferrer">github.com/alexander213213/task-api</a></li>
          <li><strong>Frontend repo:</strong> <a href="https://github.com/alexander213213/task-front" target="_blank" rel="noreferrer">github.com/alexander213213/task-front</a></li>
          <li><strong>Demo password:</strong> <code>Password123!</code></li>
        </ul>
        <p class="muted">How it flows: Post Task → Proposals → Assign Worker → Submit Work → Review.</p>
      </section>

      <section id="stack" class="block">
        <h1>What I use</h1>
        <p>
          Curious how I work? This is the stack I reach for, inspired by the whole
          <em>uses</em>-page idea.
        </p>
        <ul class="plain-list">
          <li><strong>Backend:</strong> Node.js, Express, TypeScript, REST APIs</li>
          <li><strong>Frontend:</strong> Vue 3, TypeScript, Vite, HTML/CSS</li>
          <li><strong>Database:</strong> PostgreSQL, Prisma ORM</li>
          <li><strong>Infra &amp; tools:</strong> Railway, Vercel, Zod, Git, Vitest</li>
        </ul>
      </section>

      <section id="experience" class="block">
        <h1>Background</h1>
        <p>
          I'm a self-taught developer. For the past two years I've led a small freelance team —
          building full-stack client apps, handling deploys, client communication, and project
          coordination.
        </p>
        <p>
          Most of that client work is private, but it gave me real production experience. Next up
          on my roadmap: real-time updates via SSE, more test coverage, and deployment hardening.
        </p>
      </section>

      <section id="contact" class="block">
        <h1>Get in touch</h1>
        <p>
          Open to remote opportunities. Email me at
          <a href="mailto:alexandergracilla@gmail.com"><strong>alexandergracilla@gmail.com</strong></a>
          or find me on
          <a href="https://github.com/alexander213213" target="_blank" rel="noreferrer"><strong>GitHub</strong></a>.
        </p>
        <p class="muted">Philippines · GMT+8 · Built with Vue 3 + TypeScript</p>
      </section>
    </main>
  </div>
</template>

<script setup lang="ts">
import { onMounted, ref } from 'vue'

type Theme = 'light' | 'dark'

const theme = ref<Theme>('light')
const menuOpen = ref(false)

function applyTheme(t: Theme) {
  theme.value = t
  document.documentElement.dataset.theme = t
  try {
    localStorage.setItem('theme', t)
  } catch {
    // ignore storage errors (private mode, etc.)
  }
}

function toggleTheme() {
  applyTheme(theme.value === 'light' ? 'dark' : 'light')
}

onMounted(() => {
  let initial: Theme = 'light'
  try {
    const stored = localStorage.getItem('theme')
    if (stored === 'light' || stored === 'dark') initial = stored
  } catch {
    // default to light
  }
  applyTheme(initial)
})
</script>

<style scoped>
.page {
  padding: 2rem 1.5rem;
  max-width: 1100px;
  margin: 0 auto;
}

.site-header {
  display: flex;
  justify-content: space-between;
  align-items: center;
  gap: 1rem;
}

.brand {
  display: flex;
  align-items: center;
  gap: 1rem;
  min-width: 0;
}

.avatar-link {
  flex-shrink: 0;
  display: inline-flex;
}

.avatar {
  height: 2.5rem;
  width: 2.5rem;
  border-radius: 999px;
  object-fit: cover;
  display: block;
  background: var(--border);
}

.site-name {
  display: block;
  font-weight: 800;
  font-size: 1.25rem;
  line-height: 1.1;
  letter-spacing: -0.01em;
}

.desktop-nav {
  display: none;
  margin-top: 0.75rem;
  gap: 1.5rem;
  text-transform: uppercase;
  letter-spacing: 0.08em;
  font-size: 0.75rem;
  font-weight: 600;
}

.desktop-nav a {
  color: var(--muted);
  font-weight: 600;
}

.desktop-nav a:hover {
  color: var(--link);
  text-decoration: none;
}

.header-actions {
  display: flex;
  align-items: center;
  gap: 0.75rem;
}

.theme-toggle {
  font: inherit;
  font-size: 0.75rem;
  font-weight: 700;
  text-transform: uppercase;
  letter-spacing: 0.08em;
  color: var(--muted);
  background: transparent;
  border: 1px solid var(--border);
  border-radius: 999px;
  padding: 0.4rem 0.9rem;
  cursor: pointer;
}

.theme-toggle:hover {
  color: var(--link);
  border-color: var(--muted);
}

.menu-btn {
  background: transparent;
  border: none;
  color: var(--link);
  cursor: pointer;
  padding: 0.25rem;
  display: inline-flex;
}

.menu-icon {
  height: 1.5rem;
  width: 1.5rem;
  display: block;
}

.mobile-nav {
  display: flex;
  flex-direction: column;
  gap: 1.25rem;
  padding: 1.5rem 0.5rem;
  font-weight: 700;
}

.mobile-nav a {
  color: var(--link);
}

.content {
  margin-top: 3rem;
}

.block {
  max-width: 28rem;
  margin-bottom: 3.5rem;
  scroll-margin-top: 2rem;
}

.block h1 {
  font-size: 1.5rem;
  font-weight: 800;
  letter-spacing: -0.01em;
  margin: 0 0 1rem;
  color: var(--link);
}

.block p,
.block ul {
  font-size: 1.125rem;
  line-height: 1.6;
  color: var(--text);
}

.block p + p,
.block p + ul,
.block ul + p {
  margin-top: 1.5rem;
}

.block a {
  color: var(--link);
  font-weight: 700;
  text-decoration: none;
}

.block a:hover {
  text-decoration: underline;
}

.plain-list {
  list-style: disc;
  padding-left: 1.25rem;
  display: flex;
  flex-direction: column;
  gap: 0.5rem;
}

.plain-list li::marker {
  color: var(--muted);
}

code {
  font-family: ui-monospace, SFMono-Regular, Menlo, monospace;
  font-size: 0.95em;
  background: var(--code-bg);
  border: 1px solid var(--border);
  border-radius: 4px;
  padding: 0.1em 0.35em;
}

.muted {
  color: var(--muted);
  font-size: 1rem;
}

@media (min-width: 768px) {
  .page {
    padding: 2rem 4rem;
  }
  .avatar {
    height: 3rem;
    width: 3rem;
  }
  .desktop-nav {
    display: flex;
  }
  .menu-btn,
  .mobile-nav {
    display: none;
  }
}

@media (min-width: 1024px) {
  .page {
    padding: 4rem 6rem;
  }
  .avatar {
    height: 5rem;
    width: 5rem;
  }
  .site-name {
    font-size: 1.875rem;
  }
  .content {
    padding-left: 8rem;
  }
}
</style>
