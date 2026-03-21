<template>
  <section id="projects" class="projects">
    <div class="projects-bg"></div>
    <div class="container">
      <div class="projects-header">
        <div class="section-tag">Projects</div>
        <h2 class="section-title">Featured <span>Work</span></h2>
        <p class="section-sub">A selection of projects I've built with care and attention to detail.</p>
      </div>

      <div class="filter-bar">
        <button
          v-for="tag in allTags"
          :key="tag"
          :class="['filter-btn', { active: activeFilter === tag }]"
          @click="activeFilter = tag"
        >{{ tag }}</button>
      </div>

      <div class="project-grid">
        <div
          v-for="project in filteredProjects"
          :key="project.id"
          class="project-card"
        >
          <div class="project-img-wrap">
            <img :src="project.image" :alt="project.title" class="project-img" />
            <div class="project-overlay">
              <div class="overlay-links">
                <a :href="project.demo" target="_blank" class="overlay-btn">
                  <svg width="18" height="18" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2">
                    <path d="M18 13v6a2 2 0 01-2 2H5a2 2 0 01-2-2V8a2 2 0 012-2h6M15 3h6v6M10 14L21 3"/>
                  </svg>
                  Live Demo
                </a>
                <a :href="project.github" target="_blank" class="overlay-btn overlay-btn--ghost">
                  <svg width="18" height="18" viewBox="0 0 24 24" fill="currentColor">
                    <path d="M12 0C5.374 0 0 5.373 0 12c0 5.302 3.438 9.8 8.207 11.387.599.111.793-.261.793-.577v-2.234c-3.338.726-4.033-1.416-4.033-1.416-.546-1.387-1.333-1.756-1.333-1.756-1.089-.745.083-.729.083-.729 1.205.084 1.839 1.237 1.839 1.237 1.07 1.834 2.807 1.304 3.492.997.107-.775.418-1.305.762-1.604-2.665-.305-5.467-1.334-5.467-5.931 0-1.311.469-2.381 1.236-3.221-.124-.303-.535-1.524.117-3.176 0 0 1.008-.322 3.301 1.23A11.509 11.509 0 0112 5.803c1.02.005 2.047.138 3.006.404 2.291-1.552 3.297-1.23 3.297-1.23.653 1.653.242 2.874.118 3.176.77.84 1.235 1.911 1.235 3.221 0 4.609-2.807 5.624-5.479 5.921.43.372.823 1.102.823 2.222v3.293c0 .319.192.694.801.576C20.566 21.797 24 17.3 24 12c0-6.627-5.373-12-12-12z"/>
                  </svg>
                  GitHub
                </a>
              </div>
            </div>
            <span class="project-featured" v-if="project.featured">⭐ Featured</span>
          </div>

          <div class="project-body">
            <div class="project-tags">
              <span v-for="tech in project.techs" :key="tech" class="tech-badge">{{ tech }}</span>
            </div>
            <h3 class="project-title">{{ project.title }}</h3>
            <p class="project-desc">{{ project.description }}</p>
            <div class="project-footer">
              <a :href="project.demo" target="_blank" class="btn btn-primary btn-sm">
                View Project
                <svg width="13" height="13" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.5">
                  <path d="M5 12h14M12 5l7 7-7 7"/>
                </svg>
              </a>
              <a :href="project.github" target="_blank" class="btn btn-ghost btn-sm">
                <svg width="14" height="14" viewBox="0 0 24 24" fill="currentColor">
                  <path d="M12 0C5.374 0 0 5.373 0 12c0 5.302 3.438 9.8 8.207 11.387.599.111.793-.261.793-.577v-2.234c-3.338.726-4.033-1.416-4.033-1.416-.546-1.387-1.333-1.756-1.333-1.756-1.089-.745.083-.729.083-.729 1.205.084 1.839 1.237 1.839 1.237 1.07 1.834 2.807 1.304 3.492.997.107-.775.418-1.305.762-1.604-2.665-.305-5.467-1.334-5.467-5.931 0-1.311.469-2.381 1.236-3.221-.124-.303-.535-1.524.117-3.176 0 0 1.008-.322 3.301 1.23A11.509 11.509 0 0112 5.803c1.02.005 2.047.138 3.006.404 2.291-1.552 3.297-1.23 3.297-1.23.653 1.653.242 2.874.118 3.176.77.84 1.235 1.911 1.235 3.221 0 4.609-2.807 5.624-5.479 5.921.43.372.823 1.102.823 2.222v3.293c0 .319.192.694.801.576C20.566 21.797 24 17.3 24 12c0-6.627-5.373-12-12-12z"/>
                </svg>
                GitHub
              </a>
            </div>
          </div>
        </div>
      </div>

      <div class="projects-cta">
        <p>Want to see more?</p>
        <a href="https://github.com" target="_blank" class="btn btn-ghost">
          <svg width="16" height="16" viewBox="0 0 24 24" fill="currentColor"><path d="M12 0C5.374 0 0 5.373 0 12c0 5.302 3.438 9.8 8.207 11.387.599.111.793-.261.793-.577v-2.234c-3.338.726-4.033-1.416-4.033-1.416-.546-1.387-1.333-1.756-1.333-1.756-1.089-.745.083-.729.083-.729 1.205.084 1.839 1.237 1.839 1.237 1.07 1.834 2.807 1.304 3.492.997.107-.775.418-1.305.762-1.604-2.665-.305-5.467-1.334-5.467-5.931 0-1.311.469-2.381 1.236-3.221-.124-.303-.535-1.524.117-3.176 0 0 1.008-.322 3.301 1.23A11.509 11.509 0 0112 5.803c1.02.005 2.047.138 3.006.404 2.291-1.552 3.297-1.23 3.297-1.23.653 1.653.242 2.874.118 3.176.77.84 1.235 1.911 1.235 3.221 0 4.609-2.807 5.624-5.479 5.921.43.372.823 1.102.823 2.222v3.293c0 .319.192.694.801.576C20.566 21.797 24 17.3 24 12c0-6.627-5.373-12-12-12z"/></svg>
          View All on GitHub
        </a>
      </div>
    </div>
  </section>
</template>

<script setup>
import { ref, computed } from 'vue'

const activeFilter = ref('All')

const projects = [
  {
    id: 1,
    title: 'SerWise - Restaurant Management System ',
    description: 'A full-featured capstone project for online restaurant with inventory management, kitchen management, procurements, and order tracking. Includes admin dashboard with analytics.',
    image: '/myproject/ServeWise.png',
    demo: '#',
    github: 'https://github.com/dongjrperez-netizen/RestuarantProject.git',
    techs: ['Vue.js', 'Laravel', 'MySQL', 'Vite.js'],
    category: 'Full Stack',
    featured: true,
  },
  {
    id: 2,
    title: 'Clinic Appointment System',
    description: 'A web-based system that allows patients to book appointments online while enabling clinic staff to manage schedules, patient records, and doctor availability through an admin dashboard.',
    image: '/myproject/Clinic.png',
    demo: '#',
    github: '#',
    techs: ['Vue.js', 'Vite.js', 'Laravel', 'Laragon'],
    category: 'Full Stack',
    featured: true,
  },
  {
    id: 3,
    title: 'FGS East Asia - Recruitment Platform',
    description: 'A DMW-licensed recruitment agency platform connecting skilled Filipino professionals to reputable employers worldwide, featuring job listings, applicant management, and an end-to-end overseas recruitment process.',
    image: '/myproject/FGS.png',
    demo: '#',
    github: 'https://github.com/dongjrperez-netizen/FGS_Repository.git',
    techs: ['Laravel', 'MySQL', 'Tailwind CSS', 'Alpine.js'],
    category: 'Full Stack',
  },
]

const allTags = ['All', 'Full Stack', 'Frontend', 'Backend']

const filteredProjects = computed(() =>
  activeFilter.value === 'All'
    ? projects
    : projects.filter(p => p.category === activeFilter.value)
)
</script>

<style scoped>
.projects {
  padding: 120px 0;
  position: relative;
}

.projects-bg {
  position: absolute;
  inset: 0;
  background: radial-gradient(ellipse 60% 40% at 50% 0%, rgba(167,139,250,0.05), transparent);
  pointer-events: none;
}

.projects-header {
  text-align: center;
  margin-bottom: 48px;
  position: relative;
  z-index: 1;
}

.projects-header .section-tag {
  margin: 0 auto 20px;
}

.projects-header .section-sub {
  margin: 0 auto;
}

.filter-bar {
  display: flex;
  gap: 8px;
  justify-content: center;
  margin-bottom: 48px;
  flex-wrap: wrap;
  position: relative;
  z-index: 1;
}

.filter-btn {
  font-family: var(--font-display);
  font-size: 13px;
  font-weight: 600;
  padding: 8px 20px;
  border-radius: 100px;
  background: var(--bg-card);
  color: var(--text-muted);
  border: 1px solid var(--border);
  transition: var(--transition);
  letter-spacing: 0.05em;
}

.filter-btn:hover,
.filter-btn.active {
  background: var(--accent);
  color: var(--bg);
  border-color: var(--accent);
}

.project-grid {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(340px, 1fr));
  gap: 24px;
  position: relative;
  z-index: 1;
}

.project-card {
  background: var(--bg-card);
  border: 1px solid var(--border);
  border-radius: var(--radius-lg);
  overflow: hidden;
  transition: var(--transition);
  display: flex;
  flex-direction: column;
}

.project-card:hover {
  border-color: var(--border-accent);
  transform: translateY(-4px);
  box-shadow: 0 20px 60px rgba(0,0,0,0.3), 0 0 0 1px rgba(99,209,175,0.05);
}

.project-img-wrap {
  position: relative;
  aspect-ratio: 16/10;
  overflow: hidden;
}

.project-img {
  width: 100%;
  height: 100%;
  object-fit: cover;
  transition: transform 0.5s ease;
}

.project-card:hover .project-img {
  transform: scale(1.05);
}

.project-overlay {
  position: absolute;
  inset: 0;
  background: rgba(10, 10, 15, 0.85);
  display: flex;
  align-items: center;
  justify-content: center;
  opacity: 0;
  transition: var(--transition);
  backdrop-filter: blur(4px);
}

.project-card:hover .project-overlay {
  opacity: 1;
}

.overlay-links {
  display: flex;
  gap: 12px;
  flex-direction: column;
  align-items: center;
}

.overlay-btn {
  display: inline-flex;
  align-items: center;
  gap: 8px;
  padding: 10px 20px;
  border-radius: var(--radius);
  font-family: var(--font-display);
  font-size: 13px;
  font-weight: 600;
  background: var(--accent);
  color: var(--bg);
  transition: var(--transition);
  min-width: 140px;
  justify-content: center;
}

.overlay-btn:hover { background: #7ae0bf; }

.overlay-btn--ghost {
  background: transparent;
  color: var(--text);
  border: 1px solid rgba(255,255,255,0.2);
}

.overlay-btn--ghost:hover {
  background: rgba(255,255,255,0.1);
}

.project-featured {
  position: absolute;
  top: 12px;
  left: 12px;
  font-size: 11px;
  font-weight: 600;
  background: rgba(99, 209, 175, 0.15);
  color: var(--accent);
  border: 1px solid var(--border-accent);
  padding: 4px 10px;
  border-radius: 100px;
  backdrop-filter: blur(8px);
}

.project-body {
  padding: 24px;
  display: flex;
  flex-direction: column;
  gap: 12px;
  flex: 1;
}

.project-tags {
  display: flex;
  flex-wrap: wrap;
  gap: 6px;
}

.tech-badge {
  font-size: 11px;
  font-weight: 600;
  color: var(--accent);
  background: var(--accent-glow);
  border: 1px solid var(--border-accent);
  padding: 3px 10px;
  border-radius: 100px;
  font-family: var(--font-display);
  letter-spacing: 0.03em;
}

.project-title {
  font-family: var(--font-display);
  font-size: 1.05rem;
  font-weight: 700;
  color: var(--text);
  line-height: 1.3;
}

.project-desc {
  font-size: 14px;
  color: var(--text-muted);
  line-height: 1.7;
  flex: 1;
}

.project-footer {
  display: flex;
  gap: 10px;
  padding-top: 8px;
  border-top: 1px solid var(--border);
  margin-top: 4px;
}

.projects-cta {
  text-align: center;
  margin-top: 64px;
  display: flex;
  align-items: center;
  justify-content: center;
  gap: 16px;
  color: var(--text-muted);
  font-size: 15px;
}

@media (max-width: 640px) {
  .project-grid {
    grid-template-columns: 1fr;
  }
  .projects-cta {
    flex-direction: column;
  }
}
</style>
