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
            <a href="#yapr">Projects</a>
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
      <a href="#yapr" @click="menuOpen = false">Projects</a>
      <a href="#stack" @click="menuOpen = false">Stack</a>
      <a href="#experience" @click="menuOpen = false">Experience</a>
      <a href="#contact" @click="menuOpen = false">Contact</a>
    </nav>

    <main id="top" class="content">
      <section class="block">
        <p class="kicker">Full-Stack Developer — Available for Remote Roles</p>
        <h1>Hello, I'm Alexander Gracilla.</h1>
        <p>
          I'm a <strong>full-stack developer</strong> who specializes in <strong>backend systems</strong> —
          the kind that stay correct under real-world use: encrypted protocols, guarded state
          transitions, durable storage, and APIs with predictable behavior.
        </p>
        <p>
          I design and ship with
          <strong>TypeScript, Node.js, SQLite/PostgreSQL</strong>, and terminal + web frontends
          (<strong>React Ink, Vue 3</strong>). I do my best work owning a system end to end, from
          protocol design to production deployment.
        </p>
        <p>
          My flagship project is <a href="#yapr"><strong>YAPR</strong></a> — an end-to-end encrypted
          terminal messenger with its own relay server. Details below.
        </p>
        <p>
          I also <strong>lead teams</strong>: for the past two years I've directed a small freelance
          team, driving delivery, deployments, and client communication. The fastest way to reach me
          is <a href="mailto:alexandergracilla@gmail.com"><strong>email</strong></a>; my work is on
          <a href="https://github.com/alexander213213" target="_blank" rel="noreferrer"><strong>GitHub</strong></a>.
        </p>
      </section>

      <section id="yapr" class="block">
        <p class="kicker">Featured Project</p>
        <h1>YAPR — End-to-End Encrypted Terminal Messenger</h1>
        <p>
          <strong>YAPR</strong> is a terminal messenger backed by a dedicated relay server that routes
          <strong>only ciphertext</strong> and holds messages while recipients are offline. I designed
          and built the full system across two repositories:
          <a href="https://github.com/alexander213213/yapr" target="_blank" rel="noreferrer"><strong>yapr</strong></a>
          (client) and
          <a href="https://github.com/alexander213213/yapr-server" target="_blank" rel="noreferrer"><strong>yapr-server</strong></a>
          (relay).
        </p>
        <ul class="plain-list">
          <li><strong>Designed the encryption model:</strong> per-message X25519 + AES-256-GCM using stdlib only — pairwise per member in groups of up to 50.</li>
          <li><strong>Built for reliability:</strong> persistent outbox with idempotent resends, offline inbox replay with paging, delivery acknowledgements and read receipts.</li>
          <li><strong>Defined the protocol:</strong> TLS-only newline-delimited JSON (v2) with zod-validated frames and deduplication by <code>clientMessageId</code>.</li>
          <li><strong>Hardened the server:</strong> scrypt hashing with constant-time comparison, token-bucket rate limits, 64KB frame cap, heartbeat and idle sweeps, structured logging.</li>
          <li><strong>Made storage durable:</strong> <code>node:sqlite</code> in the OS data directory with automatic migrations and pre-migration backups.</li>
          <li><strong>Shipped the terminal UI:</strong> React Ink sidebar, message threads, contacts browser, group administration, nicknames, history sharing, four themes, and a markup parser — backed by vitest suites.</li>
        </ul>
        <p>
          Getting started: <code>npm i -g @sprunkzzz/yapr</code> with a running
          yapr-server over TLS. Full specification and setup guides are in the repositories.
        </p>
        <p class="meta">
          <a href="https://github.com/alexander213213/yapr" target="_blank" rel="noreferrer">yapr repo</a>
          ·
          <a href="https://github.com/alexander213213/yapr-server" target="_blank" rel="noreferrer">yapr-server repo</a>
        </p>
      </section>

      <section id="task-marketplace" class="block">
        <p class="kicker">Additional Project</p>
        <h1>Task Marketplace Platform</h1>
        <p>
          A service marketplace where clients post tasks, workers submit proposals, owners assign a
          worker, and completed work is reviewed and rated. I built it around correctness: strictly
          guarded task states
          (<code>OPEN → ASSIGNED → SUBMITTED → COMPLETED</code>), transactional rating updates,
          JWT authentication with refresh rotation, Zod-validated contracts, and cursor-based pagination.
        </p>
        <p class="meta">
          <a href="https://tasker-demo.vercel.app" target="_blank" rel="noreferrer">Live frontend</a>
          ·
          <a href="https://github.com/alexander213213/task-api" target="_blank" rel="noreferrer">Backend API</a>
          ·
          <a href="https://github.com/alexander213213/task-front" target="_blank" rel="noreferrer">Frontend repo</a>
          · Demo password: <code>Password123!</code>
        </p>
      </section>

      <section id="stack" class="block">
        <p class="kicker">Technical Skills</p>
        <h1>Tools I work with</h1>
        <p>
          The stack behind YAPR and my marketplace work.
        </p>
        <ul class="plain-list">
          <li><strong>Backend:</strong> Node.js ≥ 22, TypeScript, Express, REST, TLS</li>
          <li><strong>Frontend:</strong> React Ink (TUI), Vue 3, Vite, HTML/CSS</li>
          <li><strong>Data:</strong> SQLite (<code>node:sqlite</code>), PostgreSQL, Prisma ORM</li>
          <li><strong>Infra &amp; tools:</strong> Docker, Railway, Zod, Pino, Vitest, Git</li>
        </ul>
      </section>

      <section id="experience" class="block">
        <p class="kicker">Experience</p>
        <h1>Background</h1>
        <p>
          I'm a self-taught developer with two years of experience <strong>leading a small
          freelance team</strong> — scoping work, coordinating delivery, managing client
          communication, and shipping full-stack applications to production.
        </p>
        <p>
          YAPR is the public record of how I work: protocol and cryptography design, server
          hardening, durable storage, terminal UI engineering, automated testing, and release
          engineering across npm, Docker, and Railway.
        </p>
      </section>

      <section id="contact" class="block">
        <p class="kicker">Contact</p>
        <h1>Get in touch</h1>
        <p>
          I am currently available for <strong>remote full-stack roles worldwide</strong>, with a
          focus on backend systems. Email me at
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
  font-family: var(--font-display);
  display: block;
  font-weight: 700;
  font-size: 1.25rem;
  line-height: 1.1;
  letter-spacing: -0.02em;
}

.desktop-nav {
  display: none;
  margin-top: 0.75rem;
  gap: 1.5rem;
  text-transform: uppercase;
  letter-spacing: 0.08em;
  font-size: 0.75rem;
  font-weight: 600;
  font-family: var(--font-mono);
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
  font-family: var(--font-mono);
  font-size: 0.75rem;
  font-weight: 600;
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
  font-family: var(--font-display);
}

.mobile-nav a {
  color: var(--link);
}

.content {
  margin-top: 3rem;
}

.block {
  max-width: 36rem;
  margin-bottom: 3.5rem;
  scroll-margin-top: 2rem;
}

.kicker {
  font-family: var(--font-mono);
  font-size: 0.75rem;
  font-weight: 600;
  letter-spacing: 0.12em;
  text-transform: uppercase;
  color: var(--muted);
  margin: 0 0 0.5rem;
}

.block h1 {
  font-family: var(--font-display);
  font-size: clamp(1.75rem, 1.3rem + 1.5vw, 2.25rem);
  font-weight: 700;
  letter-spacing: -0.03em;
  line-height: 1.1;
  margin: 0 0 1rem;
  color: var(--link);
  text-wrap: balance;
}

.block p,
.block ul {
  font-size: 1.0625rem;
  line-height: 1.75;
  color: var(--text);
}

.block p + p,
.block p + ul,
.block ul + p {
  margin-top: 1.5rem;
}

.block a {
  color: var(--link);
  font-weight: 600;
  text-decoration: none;
  text-decoration-thickness: 1px;
  text-underline-offset: 3px;
}

.block a:hover {
  text-decoration: underline;
}

.plain-list {
  list-style: disc;
  padding-left: 1.25rem;
  display: flex;
  flex-direction: column;
  gap: 0.6rem;
}

.plain-list li::marker {
  color: var(--muted);
}

code {
  font-family: var(--font-mono);
  font-size: 0.875em;
  background: var(--code-bg);
  border: 1px solid var(--border);
  border-radius: 6px;
  padding: 0.12em 0.4em;
  white-space: nowrap;
}

.meta {
  font-size: 0.95rem;
}

.meta a {
  white-space: nowrap;
}

.muted {
  font-family: var(--font-mono);
  color: var(--muted);
  font-size: 0.85rem;
  letter-spacing: 0.01em;
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
    font-size: clamp(1.5rem, 1.2rem + 1vw, 1.875rem);
  }
  .content {
    padding-left: 8rem;
  }
}
</style>
