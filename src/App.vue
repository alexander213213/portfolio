<template>
  <div class="portfolio">

    <nav class="sidebar-nav">
      <div class="nav-logo">
        <span class="nav-logo-initials">AG</span>
      </div>
      <div class="nav-links">
        <a
          v-for="item in navItems"
          :key="item.id"
          :href="`#${item.id}`"
          class="nav-link"
          :class="{ active: activeSection === item.id }"
          @click.prevent="scrollTo(item.id)"
        >
          <span class="nav-link-dot" />
          <span class="nav-link-label">{{ item.label }}</span>
        </a>
      </div>
    </nav>

    <main class="main-content">

      <section id="hero" class="section hero-section">
        <div class="hero-eyebrow reveal">
          <n-tag :bordered="true" round class="accent-tag">Full-Stack Developer</n-tag>
          <div class="eyebrow-line" />
        </div>

        <div class="hero-body">
          <div class="reveal reveal-delay-1">
            <h1 class="hero-name">Alexander T.<br><span class="accent-text">Gracilla</span></h1>
          </div>

          <div class="hero-meta reveal reveal-delay-2">
            <n-grid :cols="3" :x-gap="0" responsive="self" :collapsed-cols="3">
              <n-gi>
                <div class="hero-stat-item">
                  <n-statistic label="location">
                    <template #default><span class="stat-val">Philippines</span></template>
                    <template #suffix><span class="stat-suffix">GMT+8</span></template>
                  </n-statistic>
                </div>
              </n-gi>
              <n-gi>
                <div class="hero-stat-item bordered">
                  <n-statistic label="focus">
                    <template #default><span class="stat-val">Backend</span></template>
                    <template #suffix><span class="stat-suffix">+ Full-Stack</span></template>
                  </n-statistic>
                </div>
              </n-gi>
              <n-gi>
                <div class="hero-stat-item bordered">
                  <n-statistic label="availability">
                    <template #default><span class="stat-val">Remote</span></template>
                    <template #suffix><span class="stat-suffix">Worldwide</span></template>
                  </n-statistic>
                </div>
              </n-gi>
            </n-grid>
          </div>

          <div class="reveal reveal-delay-3">
            <n-text class="hero-bio" depth="3">
              I build reliable web applications using TypeScript, Node.js, PostgreSQL,
              and modern frontend frameworks. My focus is on backend architecture,
              data integrity, and predictable application workflows.
            </n-text>
            <n-text class="hero-bio" depth="3" style="display:block; margin-top: 12px">
              Recently, I developed a Task Marketplace platform — a full-stack system
              demonstrating guarded state transitions, transactional data consistency,
              authentication flows, and scalable API design.
            </n-text>
          </div>

          <n-space :size="12" class="reveal reveal-delay-4" style="margin-top: 32px" :wrap="true">
            <n-button type="primary" class="primary-btn" tag="a" href="#project">View Project</n-button>
            <n-button ghost class="secondary-btn" tag="a" href="#contact">Get in Touch</n-button>
            <n-button ghost class="secondary-btn" tag="a" href="https://github.com/alexander213213" target="_blank">GitHub ↗</n-button>
          </n-space>
        </div>
      </section>

      <n-divider class="section-divider" />

      <section id="project" class="section">
        <div class="section-heading reveal">
          <p class="section-label">Featured Project</p>
          <h2>Task Marketplace Platform</h2>
        </div>

        <div class="reveal reveal-delay-1">
          <n-text depth="3" class="section-intro">
            A full-stack marketplace where users can post tasks, submit proposals,
            assign workers, and leave reviews after work is completed. The platform
            models a simplified service marketplace while emphasizing correct state
            management, transactional operations, and backend reliability.
          </n-text>
        </div>

        <n-card class="demo-card reveal reveal-delay-2" :bordered="true">
          <template #header>
            <div class="card-header-row">
              <span class="card-title">Demo Environment</span>
              <n-tag size="small" class="accent-tag">Live</n-tag>
            </div>
          </template>
          <n-text depth="3">
            The demo environment includes seed data to showcase platform workflows.
            All demo accounts use the password:
          </n-text>
          <div class="password-box">
            <code class="password-code">Password123!</code>
          </div>
          <n-space :size="12" style="margin-top: 20px" :wrap="true">
            <n-button tag="a" href="https://tasker-demo.vercel.app" target="_blank" type="primary" class="primary-btn" size="small">Frontend Demo ↗</n-button>
            <n-button tag="a" href="https://github.com/alexander213213/task-api" target="_blank" ghost class="secondary-btn" size="small">Backend API ↗</n-button>
            <n-button tag="a" href="https://github.com/alexander213213/task-front" target="_blank" ghost class="secondary-btn" size="small">Repository ↗</n-button>
          </n-space>
        </n-card>

        <div class="reveal reveal-delay-3">
          <p class="section-label" style="margin-bottom: 16px">System Workflow</p>
          <div class="workflow-strip">
            <n-grid :cols="5" :x-gap="0" responsive="self" :collapsed-cols="1">
              <n-gi v-for="(step, i) in workflowSteps" :key="step.label">
                <div class="workflow-cell" :class="{ 'workflow-cell-last': i === workflowSteps.length - 1 }">
                  <div class="workflow-step-num">{{ String(i + 1).padStart(2, '0') }}</div>
                  <div class="workflow-step-label">{{ step.label }}</div>
                  <n-text class="workflow-step-desc" depth="3">{{ step.desc }}</n-text>
                </div>
              </n-gi>
            </n-grid>
          </div>
        </div>
      </section>

      <n-divider class="section-divider" />

      <section id="features" class="section">
        <div class="section-heading reveal">
          <p class="section-label">Core Features</p>
          <h2>What the platform does</h2>
        </div>

        <n-grid :cols="2" :x-gap="16" :y-gap="16" responsive="self" :collapsed-cols="1">
          <n-gi v-for="(feat, i) in coreFeatures" :key="feat.title">
            <n-card
              class="feature-card reveal"
              :class="`reveal-delay-${(i % 4) + 1}`"
              :bordered="true"
            >
              <template #header>
                <div class="card-header-row">
                  <span class="card-title">{{ feat.title }}</span>
                  <div class="feature-num">{{ String(i + 1).padStart(2, '0') }}</div>
                </div>
              </template>
              <n-text depth="3">{{ feat.desc }}</n-text>
              <div v-if="feat.points" class="feature-points">
                <div v-for="pt in feat.points" :key="pt" class="feature-point">
                  <span class="point-bullet" />
                  <n-text depth="3">{{ pt }}</n-text>
                </div>
              </div>
            </n-card>
          </n-gi>
        </n-grid>
      </section>

      <n-divider class="section-divider" />

      <section id="technical" class="section">
        <div class="section-heading reveal">
          <p class="section-label">Technical Highlights</p>
          <h2>Engineering decisions</h2>
        </div>

        <n-grid :cols="3" :x-gap="16" :y-gap="16" responsive="self" :collapsed-cols="1">
          <n-gi v-for="(item, i) in techHighlights" :key="item.title">
            <n-card
              class="highlight-card reveal"
              :class="`reveal-delay-${i + 1}`"
              :bordered="true"
            >
              <template #header>
                <div>
                  <div class="highlight-num">{{ String(i + 1).padStart(2, '0') }}</div>
                  <span class="card-title">{{ item.title }}</span>
                </div>
              </template>
              <n-text depth="3">{{ item.challenge }}</n-text>
              <n-divider style="margin: 14px 0" />
              <p class="approach-label">Approach</p>
              <n-text depth="3">{{ item.approach }}</n-text>
            </n-card>
          </n-gi>
        </n-grid>

        <div class="arch-block reveal" style="margin-top: 32px">
          <p class="section-label" style="margin-bottom: 16px">Architecture</p>
          <div class="arch-strip">
            <div v-for="(layer, i) in archLayers" :key="layer" class="arch-layer">
              <span class="arch-layer-text">{{ layer }}</span>
              <span v-if="i < archLayers.length - 1" class="arch-arrow">→</span>
            </div>
          </div>
        </div>
      </section>

      <n-divider class="section-divider" />

      <section id="stack" class="section">
        <div class="section-heading centered reveal">
          <p class="section-label">Technology Stack</p>
          <h2>Tools used</h2>
        </div>

        <n-grid :cols="4" :x-gap="16" :y-gap="16" responsive="self" :collapsed-cols="2" class="reveal reveal-delay-1">
          <n-gi v-for="group in stackGroups" :key="group.label">
            <n-card class="stack-card" :bordered="true">
              <template #header><span class="stack-group-label">{{ group.label }}</span></template>
              <n-space vertical :size="8">
                <n-tag
                  v-for="tech in group.items"
                  :key="tech"
                  round
                  class="accent-tag stack-item-tag"
                  style="width: 100%; justify-content: flex-start"
                >
                  {{ tech }}
                </n-tag>
              </n-space>
            </n-card>
          </n-gi>
        </n-grid>
      </section>

      <n-divider class="section-divider" />

      <section id="experience" class="section">
        <div class="section-heading reveal">
          <p class="section-label">Experience</p>
          <h2>Background</h2>
        </div>

        <n-grid :cols="2" :x-gap="32" responsive="self" :collapsed-cols="1">
          <n-gi>
            <div class="reveal reveal-delay-1">
              <n-text depth="3" class="exp-body">
                I am a self-taught full-stack developer who has led a small freelance
                development team over the past two years. During this time, we delivered
                multiple client projects involving full-stack web applications. My role
                included both technical implementation and project coordination.
              </n-text>
              <n-text depth="3" class="exp-body" style="display:block; margin-top: 14px">
                Although most client work is private due to ownership agreements, this
                experience provided hands-on exposure to production deployments, client
                communication, system implementation, and team collaboration.
              </n-text>
            </div>
          </n-gi>
          <n-gi>
            <div class="reveal reveal-delay-2">
              <p class="section-label" style="margin-bottom: 14px">Skills</p>
              <n-grid :cols="2" :x-gap="12" :y-gap="12" responsive="self" :collapsed-cols="1">
                <n-gi v-for="group in skillGroups" :key="group.label">
                  <div class="skill-group">
                    <p class="skill-group-label">{{ group.label }}</p>
                    <div class="skill-tags">
                      <n-tag
                        v-for="sk in group.items"
                        :key="sk"
                        size="small"
                        round
                        class="accent-tag"
                      >{{ sk }}</n-tag>
                    </div>
                  </div>
                </n-gi>
              </n-grid>
            </div>
          </n-gi>
        </n-grid>

        <n-card class="improvements-card reveal reveal-delay-3" :bordered="true" style="margin-top: 32px">
          <template #header>
            <div class="card-header-row">
              <span class="card-title">Planned Improvements</span>
              <n-tag size="small" class="accent-tag muted-tag">Roadmap</n-tag>
            </div>
          </template>
          <n-grid :cols="2" :x-gap="24" responsive="self" :collapsed-cols="1">
            <n-gi v-for="item in plannedItems" :key="item">
              <div class="planned-item">
                <span class="point-bullet" />
                <n-text depth="3">{{ item }}</n-text>
              </div>
            </n-gi>
          </n-grid>
        </n-card>
      </section>

      <n-divider class="section-divider" />

      <section id="contact" class="section contact-section">
        <n-card class="contact-card" :bordered="true">
          <div class="contact-inner">
            <div class="contact-accent-col">
              <div class="contact-accent-line" />
            </div>
            <div class="contact-content">
              <p class="section-label">Contact</p>
              <h2>Open to remote opportunities</h2>
              <n-text depth="3" class="contact-body">
                I'm available for remote junior backend and full-stack roles worldwide.
                Feel free to reach out via email or GitHub.
              </n-text>

              <div class="contact-details">
                <div class="contact-row">
                  <span class="contact-label">Email</span>
                  <a href="mailto:alexandergracilla@gmail.com" class="contact-link">
                    alexandergracilla@gmail.com
                  </a>
                </div>
                <div class="contact-row">
                  <span class="contact-label">GitHub</span>
                  <a href="https://github.com/alexander213213" target="_blank" class="contact-link">github.com/alexander213213 ↗</a>
                </div>
                <div class="contact-row">
                  <span class="contact-label">Location</span>
                  <n-text depth="3">Philippines · GMT+8</n-text>
                </div>
              </div>

              <n-space :size="12" style="margin-top: 28px" :wrap="true">
                <n-button type="primary" class="primary-btn" tag="a" href="mailto:alexandergracilla@gmail.com">
                  Send Email
                </n-button>
                <n-button ghost class="secondary-btn" tag="a" href="https://github.com/alexander213213" target="_blank">
                  GitHub ↗
                </n-button>
              </n-space>
            </div>
          </div>
        </n-card>

        <p class="footer-note">
          <n-text depth="3">Built with Vue 3 · Naive UI · TypeScript</n-text>
        </p>
      </section>

    </main>
  </div>
</template>

<script setup lang="ts">
import { ref, onMounted, onUnmounted } from 'vue'

// ─── NAV ───────────────────────────────────────────────────────────────────
const navItems = [
  { id: 'hero',       label: 'Intro'      },
  { id: 'project',   label: 'Project'    },
  { id: 'features',  label: 'Features'   },
  { id: 'technical', label: 'Technical'  },
  { id: 'stack',     label: 'Stack'      },
  { id: 'experience',label: 'Experience' },
  { id: 'contact',   label: 'Contact'    },
]

const activeSection = ref('hero')

function scrollTo(id: string) {
  document.getElementById(id)?.scrollIntoView({ behavior: 'smooth' })
}

function onScroll() {
  for (const item of [...navItems].reverse()) {
    const el = document.getElementById(item.id)
    if (el && el.getBoundingClientRect().top <= 120) {
      activeSection.value = item.id
      return
    }
  }
  activeSection.value = 'hero'
}

function initReveal() {
  const els = document.querySelectorAll('.reveal')
  const observer = new IntersectionObserver(
    (entries) => {
      entries.forEach(e => { if (e.isIntersecting) { (e.target as HTMLElement).classList.add('revealed'); observer.unobserve(e.target) } })
    },
    { threshold: 0.1, rootMargin: '0px 0px -40px 0px' }
  )
  els.forEach(el => observer.observe(el))
}

onMounted(() => {
  window.addEventListener('scroll', onScroll, { passive: true })
  initReveal()
})
onUnmounted(() => window.removeEventListener('scroll', onScroll))

const workflowSteps = [
  { label: 'Post Task',      desc: 'User creates and publishes a task with a reward' },
  { label: 'Proposals',      desc: 'Workers submit proposals for the task' },
  { label: 'Assign Worker',  desc: 'Owner selects and assigns a worker' },
  { label: 'Submit Work',    desc: 'Worker completes and submits' },
  { label: 'Review',         desc: 'Owner reviews and rates the worker' },
]

const coreFeatures = [
  {
    title: 'Guarded Task Lifecycle',
    desc: 'Tasks follow a strictly controlled lifecycle. State checks ensure tasks cannot skip stages or enter invalid states, preventing inconsistent behavior.',
    points: ['OPEN → ASSIGNED → SUBMITTED → COMPLETED', 'OPEN → CANCELLED'],
  },
  {
    title: 'Proposal System',
    desc: 'Workers can submit proposals for any open task. Owners review and select a worker through a controlled assignment flow.',
    points: ['Multiple proposals per task', 'Owner-controlled selection', 'Proposal status tracking'],
  },
  {
    title: 'Review & Rating System',
    desc: 'Once a task is completed, the owner can leave a review. Worker ratings are recalculated inside database transactions to ensure consistency.',
    points: ['Reviews only on completed tasks', 'Atomic rating recalculation', 'Transaction-backed updates'],
  },
  {
    title: 'Authentication & Authorization',
    desc: 'JWT access tokens with refresh token rotation and client-side retry logic. Authorization rules enforce strict resource ownership.',
    points: ['JWT + refresh tokens', 'Auto token refresh on expiry', 'Per-action ownership checks'],
  },
  {
    title: 'Cursor-Based Pagination',
    desc: 'The API uses cursor-based pagination instead of offset pagination for stable, performant results even as datasets change.',
    points: ['Stable across data changes', 'Better performance at scale', 'Consistent ordering'],
  },
  {
    title: 'Input Validation',
    desc: 'All API requests are validated using Zod schemas, ensuring early rejection of invalid input and consistent API contracts.',
    points: ['Zod schema validation', 'Early request rejection', 'Consistent API contracts'],
  },
]

const techHighlights = [
  {
    title: 'Task Workflow Integrity',
    challenge: 'Task-based systems can easily allow invalid updates if state transitions are not strictly enforced.',
    approach: 'Implemented guarded state transitions so actions are only allowed when the task is in the correct state.',
  },
  {
    title: 'Consistent Rating Calculations',
    challenge: 'Worker ratings must remain accurate even when multiple reviews occur concurrently.',
    approach: 'Used database transactions to ensure review creation and rating updates occur atomically.',
  },
  {
    title: 'Scalable Pagination',
    challenge: 'Offset pagination becomes inefficient and unstable when records are inserted or deleted.',
    approach: 'Implemented cursor-based pagination for more predictable and scalable queries.',
  },
]

const archLayers = ['Vue 3 Client', 'Express REST API', 'Service Logic', 'Prisma ORM', 'PostgreSQL']

const stackGroups = [
  { label: 'Backend',     items: ['Node.js', 'Express', 'TypeScript', 'REST API'] },
  { label: 'Frontend',    items: ['Vue 3', 'TypeScript', 'Naive UI', 'Vite'] },
  { label: 'Database',    items: ['PostgreSQL', 'Prisma ORM'] },
  { label: 'Infra & Tools', items: ['Railway', 'Vercel', 'Zod', 'Git', 'Vitest'] },
]

const skillGroups = [
  { label: 'Languages',  items: ['TypeScript', 'JavaScript', 'SQL'] },
  { label: 'Backend',    items: ['Node.js', 'Express', 'REST APIs', 'Auth systems'] },
  { label: 'Frontend',   items: ['Vue 3', 'React', 'HTML', 'CSS'] },
  { label: 'Database',   items: ['PostgreSQL', 'Prisma ORM'] },
]

const plannedItems = [
  'Real-time task updates via Server-Sent Events (SSE)',
  'Expanded automated test coverage',
  'Additional UI improvements',
  'Deployment hardening and monitoring',
]
</script>

<style scoped>
* { box-sizing: border-box; }

.portfolio {
  display: flex;
  min-height: 100vh;
  background: linear-gradient(180deg, rgba(17, 18, 22, 0.98) 0%, rgba(22, 23, 28, 1) 100%);
  color: #d7d9df;
  font-family: 'Helvetica Neue', sans-serif;
}

.sidebar-nav {
  position: fixed;
  top: 0;
  left: 0;
  width: 200px;
  height: 100vh;
  border-right: 1px solid rgba(120, 123, 134, 0.12);
  background: rgba(11, 12, 15, 0.7);
  backdrop-filter: blur(12px);
  display: flex;
  flex-direction: column;
  padding: 32px 0;
  z-index: 100;
}

.nav-logo {
  padding: 0 24px 32px;
  border-bottom: 1px solid rgba(120, 123, 134, 0.1);
  margin-bottom: 24px;
}

.nav-logo-initials {
  display: inline-flex;
  align-items: center;
  justify-content: center;
  padding: 10px;
  border: 1px solid rgba(86, 214, 187, 0.35);
  color: #56d6bb;
  font-size: 0.9rem;
  font-weight: 700;
  letter-spacing: 0.08em;
  text-align: center;
  background: rgba(86, 214, 187, 0.04);
}

.nav-links {
  display: flex;
  flex-direction: column;
  gap: 2px;
  padding: 0 12px;
}

.nav-link {
  display: flex;
  align-items: center;
  gap: 10px;
  padding: 9px 12px;
  text-decoration: none;
  color: #6e7480;
  font-size: 0.84rem;
  letter-spacing: 0.02em;
  transition: color 0.2s;
  border-radius: 2px;
}

.nav-link:hover { color: #c8cdd8; }

.nav-link.active { color: #56d6bb; }

.nav-link-dot {
  width: 5px;
  height: 5px;
  border-radius: 999px;
  background: currentColor;
  flex-shrink: 0;
  opacity: 0.5;
  transition: opacity 0.2s, transform 0.2s;
}

.nav-link.active .nav-link-dot {
  opacity: 1;
  transform: scale(1.4);
}

.main-content {
  margin-left: 200px;
  flex: 1;
  min-width: 0;
}

.section {
  width: 100%;
  padding: 72px 56px 40px;
  border-bottom: 1px solid rgba(120, 123, 134, 0.1);
}

.section:last-child { border-bottom: none; }

.section-divider {
  --n-color: rgba(120, 123, 134, 0.1) !important;
  margin: 0 !important;
}

.reveal {
  opacity: 0;
  transform: translateY(18px);
  transition: opacity 0.55s ease, transform 0.55s ease;
}

.reveal.revealed { opacity: 1; transform: translateY(0); }

.reveal-delay-1 { transition-delay: 0.08s; }
.reveal-delay-2 { transition-delay: 0.16s; }
.reveal-delay-3 { transition-delay: 0.24s; }
.reveal-delay-4 { transition-delay: 0.32s; }

.section-label {
  margin: 0;
  font-size: 0.75rem;
  letter-spacing: 0.14em;
  text-transform: uppercase;
  color: #56d6bb;
  font-weight: 600;
}

.section-heading { margin-bottom: 28px; }
.section-heading.centered { text-align: center; }

.section-heading h2 {
  margin: 8px 0 0;
  font-size: clamp(1.8rem, 3vw, 2.8rem);
  font-weight: 600;
  color: #eef1f6;
  letter-spacing: -0.03em;
}

.section-intro {
  display: block;
  max-width: 680px;
  line-height: 1.85;
  margin-bottom: 32px;
}

/* Naive UI overrides */
.accent-tag {
  --n-border: 1px solid rgba(86, 214, 187, 0.35) !important;
  --n-text-color: #56d6bb !important;
  --n-color: rgba(86, 214, 187, 0.06) !important;
}

.muted-tag {
  --n-border: 1px solid rgba(120, 123, 134, 0.3) !important;
  --n-text-color: #8d93a1 !important;
  --n-color: rgba(120, 123, 134, 0.06) !important;
}

.primary-btn {
  --n-color: #56d6bb !important;
  --n-color-hover: #67ddc4 !important;
  --n-color-pressed: #46c8ad !important;
  --n-text-color: #111318 !important;
  --n-border: 1px solid #56d6bb !important;
  font-weight: 600;
}

.secondary-btn {
  --n-text-color: #56d6bb !important;
  --n-border: 1px solid rgba(86, 214, 187, 0.35) !important;
  --n-border-hover: 1px solid rgba(86, 214, 187, 0.55) !important;
  --n-border-pressed: 1px solid rgba(86, 214, 187, 0.55) !important;
}

/* cards */
.demo-card,
.feature-card,
.highlight-card,
.stack-card,
.improvements-card,
.contact-card {
  --n-color: rgba(12, 13, 17, 0.42) !important;
  --n-border-color: rgba(120, 123, 134, 0.16) !important;
  --n-border-radius: 0 !important;
  --n-padding-top: 20px !important;
  --n-padding-bottom: 20px !important;
  --n-padding-left: 22px !important;
  --n-padding-right: 22px !important;
}

.contact-card {
  --n-padding-top: 0 !important;
  --n-padding-bottom: 0 !important;
  --n-padding-left: 0 !important;
  --n-padding-right: 0 !important;
}

.card-header-row {
  display: flex;
  align-items: center;
  justify-content: space-between;
  gap: 12px;
}

.card-title {
  color: #eef1f6;
  font-size: 1.05rem;
  font-weight: 600;
}

.hero-section { padding-top: 80px; }

.hero-eyebrow {
  display: flex;
  align-items: center;
  gap: 16px;
  margin-bottom: 40px;
}

.eyebrow-line {
  flex: 1;
  height: 1px;
  background: linear-gradient(90deg, rgba(86, 214, 187, 0.3) 0%, transparent 100%);
}

.hero-name {
  font-size: clamp(3.2rem, 7vw, 6rem);
  font-weight: 700;
  line-height: 1.0;
  letter-spacing: -0.05em;
  color: #eef1f6;
  margin: 0 0 32px;
}

.accent-text { color: #56d6bb; }

.hero-meta {
  margin-bottom: 28px;
  border: 1px solid rgba(120, 123, 134, 0.16);
  background: rgba(12, 13, 17, 0.45);
}

.hero-stat-item {
  padding: 16px 20px;
}

.hero-stat-item.bordered {
  border-left: 1px solid rgba(120, 123, 134, 0.16);
}

.stat-val {
  font-size: 1rem;
  font-weight: 600;
  color: #eef1f6;
  text-transform: uppercase;
  letter-spacing: 0.04em;
}

.stat-suffix {
  font-size: 0.8rem;
  color: #6e7480;
  margin-left: 6px;
}

:deep(.n-statistic-label) {
  color: #8d93a1 !important;
  font-size: 0.78rem !important;
  text-transform: uppercase;
  letter-spacing: 0.08em;
}

.hero-bio {
  display: block;
  max-width: 620px;
  line-height: 1.85;
  font-size: 1rem;
}

.workflow-strip {
  border: 1px solid rgba(120, 123, 134, 0.16);
  background: rgba(8, 9, 12, 0.4);
}

.workflow-cell {
  padding: 22px 20px;
  border-right: 1px solid rgba(120, 123, 134, 0.12);
  height: 100%;
  box-sizing: border-box;
}

.workflow-cell-last { border-right: none; }

.workflow-step-num {
  display: inline-block;
  font-size: 0.72rem;
  font-weight: 700;
  color: #56d6bb;
  letter-spacing: 0.1em;
  margin-bottom: 8px;
}

.workflow-step-label {
  font-size: 0.95rem;
  font-weight: 600;
  color: #eef1f6;
  margin-bottom: 8px;
}

.workflow-step-desc {
  display: block;
  font-size: 0.85rem;
  line-height: 1.6;
}

.demo-card { margin-bottom: 40px; }

.password-box {
  margin-top: 14px;
  padding: 6px 8px;
  border: 1px solid rgba(86, 214, 187, 0.2);
  background: rgba(86, 214, 187, 0.03);
  display: inline-block;
}

.password-code {
  font-family: monospace;
  font-size: 1rem;
  color: #56d6bb;
  letter-spacing: 0.06em;
}

.feature-num {
  font-size: 0.72rem;
  font-weight: 700;
  color: #56d6bb;
  letter-spacing: 0.1em;
}

.feature-points {
  margin-top: 14px;
  display: flex;
  flex-direction: column;
  gap: 8px;
  padding-top: 14px;
  border-top: 1px solid rgba(120, 123, 134, 0.12);
}

.feature-point {
  display: flex;
  align-items: flex-start;
  gap: 10px;
}

.point-bullet {
  width: 6px;
  height: 6px;
  flex-shrink: 0;
  border-radius: 999px;
  background: #56d6bb;
  margin-top: 6px;
}

.highlight-num {
  font-size: 0.72rem;
  font-weight: 700;
  color: #56d6bb;
  letter-spacing: 0.1em;
  margin-bottom: 6px;
}

.approach-label {
  margin: 0 0 6px;
  font-size: 0.75rem;
  letter-spacing: 0.1em;
  text-transform: uppercase;
  color: #56d6bb;
  font-weight: 600;
}

/* Architecture strip */
.arch-strip {
  display: flex;
  align-items: center;
  gap: 0;
  border: 1px solid rgba(120, 123, 134, 0.16);
  background: rgba(8, 9, 12, 0.4);
  padding: 0;
  width: fit-content;
}

.arch-layer {
  display: flex;
  align-items: center;
  gap: 0;
}

.arch-layer-text {
  padding: 14px 22px;
  font-size: 0.85rem;
  font-weight: 600;
  color: #c8cdd8;
  border-right: 1px solid rgba(120, 123, 134, 0.12);
  white-space: nowrap;
}

.arch-arrow {
  padding: 14px 10px;
  color: #56d6bb;
  font-size: 0.9rem;
  border-right: 1px solid rgba(120, 123, 134, 0.12);
}

.arch-layer:last-child .arch-layer-text { border-right: none; }
.arch-layer:last-child .arch-arrow { display: none; }

.stack-group-label {
  color: #eef1f6;
  font-size: 0.9rem;
  font-weight: 600;
}

.stack-item-tag {
  --n-height: 28px !important;
}

.exp-body {
  display: block;
  line-height: 1.85;
}

.skill-group { margin-bottom: 8px; }

.skill-group-label {
  margin: 0 0 8px;
  font-size: 0.75rem;
  letter-spacing: 0.1em;
  text-transform: uppercase;
  color: #7f8794;
  font-weight: 600;
}

.skill-tags {
  display: flex;
  flex-wrap: wrap;
  gap: 6px;
}

.planned-item {
  display: flex;
  align-items: flex-start;
  gap: 10px;
  padding: 6px 0;
}

.contact-section { padding-bottom: 72px; }

.contact-inner {
  display: grid;
  grid-template-columns: 48px 1fr;
}

.contact-accent-col {
  border-right: 1px solid rgba(120, 123, 134, 0.14);
  display: flex;
  align-items: stretch;
}

.contact-accent-line {
  width: 2px;
  margin: 0 auto;
  background: linear-gradient(180deg, transparent 0%, rgba(86, 214, 187, 0.5) 25%, rgba(86, 214, 187, 0.5) 75%, transparent 100%);
}

.contact-content {
  padding: 40px 44px;
}

.contact-content h2 {
  margin: 8px 0 16px;
  font-size: clamp(1.6rem, 3vw, 2.4rem);
  font-weight: 600;
  color: #eef1f6;
  letter-spacing: -0.03em;
}

.contact-body {
  display: block;
  max-width: 540px;
  line-height: 1.85;
  margin-bottom: 28px;
}

.contact-details {
  display: flex;
  flex-direction: column;
  gap: 10px;
}

.contact-row {
  display: flex;
  align-items: center;
  gap: 16px;
}

.contact-label {
  font-size: 0.78rem;
  letter-spacing: 0.1em;
  text-transform: uppercase;
  color: #7f8794;
  font-weight: 600;
  min-width: 64px;
}

.contact-link {
  color: #56d6bb;
  text-decoration: none;
  font-size: 0.95rem;
  transition: opacity 0.2s;
}

.contact-link:hover { opacity: 0.75; }

.footer-note {
  text-align: center;
  margin-top: 32px;
  font-size: 0.82rem;
}

@media (max-width: 1100px) {
  .sidebar-nav { width: 160px; }
  .main-content { margin-left: 160px; }
  .section { padding: 56px 36px 32px; }
}

@media (max-width: 860px) {
  .sidebar-nav { display: none; }
  .main-content { margin-left: 0; }
  .section { padding: 48px 24px 28px; }
  .workflow-cell { border-right: none; border-bottom: 1px solid rgba(120, 123, 134, 0.12); }
  .workflow-cell-last { border-bottom: none; }
  .arch-strip { flex-direction: column; width: 100%; }
  .arch-layer-text { border-right: none; border-bottom: 1px solid rgba(120, 123, 134, 0.12); width: 100%; }
  .arch-arrow { transform: none; padding: 6px 22px; border-right: none; border-bottom: 1px solid rgba(120, 123, 134, 0.12); }
  .contact-inner { grid-template-columns: 1fr; }
  .contact-accent-col { display: none; }
  .contact-content { padding: 28px 20px; }
}

@media (max-width: 640px) {
  .section { padding: 40px 16px 24px; }
  .hero-name { font-size: clamp(2.6rem, 12vw, 3.8rem); }
}
</style>