<template>
  <section id="home" class="hero">
    <!-- Background grid -->
    <div class="hero-grid"></div>
    <!-- Glowing orbs -->
    <div class="orb orb-1"></div>
    <div class="orb orb-2"></div>

    <div class="container hero-inner">
      <div class="hero-content">
        <div class="hero-badge fade-up" style="animation-delay:0.1s">
          <span class="status-dot"></span>
          Available for work
        </div>

        <h1 class="hero-title fade-up" style="animation-delay:0.2s">
          Hi, I'm <span class="name-highlight">Roger</span>
          <br />
          <span class="title-line">
            <span class="typed-wrapper">
              <span class="typed-text">{{ displayedTitle }}</span>
              <span class="cursor" :class="{ blink: !isTyping }">|</span>
            </span>
          </span>
        </h1>

        <p class="hero-desc fade-up" style="animation-delay:0.35s">
          I craft elegant digital experiences with clean code and a
          passion for performance. Specializing in modern web
          technologies — from pixel-perfect frontends to scalable backends.
        </p>

        <div class="hero-actions fade-up" style="animation-delay:0.5s">
          <a href="#projects" class="btn btn-primary">
            View My Work
            <svg width="16" height="16" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.5">
              <path d="M5 12h14M12 5l7 7-7 7"/>
            </svg>
          </a>
          <a href="#contact" class="btn btn-ghost">Let's Talk</a>
        </div>
<!-- 
        <div class="hero-stats fade-up" style="animation-delay:0.65s">
          <div v-for="stat in stats" :key="stat.label" class="stat">
            <span class="stat-num">{{ stat.num }}</span>
            <span class="stat-label">{{ stat.label }}</span>
          </div>
        </div> -->
      </div>

      <div class="hero-visual fade-up" style="animation-delay:0.3s">
        <div class="profile-frame">
          <div class="profile-rings">
            <div class="ring ring-1"></div>
            <div class="ring ring-2"></div>
          </div>
          <div class="profile-img-wrap">
            <img
              src="/profile.jpg"
              alt="Alex Rivera"
              class="profile-img"
            />
          </div>
          <div class="badge-card badge-card--tl">
            <span class="badge-icon">⚡</span>
            <div>
              <div class="badge-title">Fast Dev</div>
              <div class="badge-sub">Clean Code</div>
            </div>
          </div>
        </div>
      </div>
    </div>

    <div class="scroll-hint">
      <div class="scroll-mouse">
        <div class="scroll-wheel"></div>
      </div>
      <span>Scroll down</span>
    </div>
  </section>
</template>

<script setup>
import { ref, onMounted } from 'vue'

const titles = ['Web Developer', 'Full Stack Developer', 'Vue.js Specialist', 'Laravel Expert']
let titleIndex = 0
let charIndex = 0
const displayedTitle = ref('')
const isTyping = ref(true)
let timeout = null

const stats = [
  { num: '5+', label: 'Years Exp.' },
  { num: '50+', label: 'Projects' },
  { num: '30+', label: 'Clients' },
  { num: '99%', label: 'Satisfaction' },
]

function typeTitle() {
  const current = titles[titleIndex]
  if (charIndex < current.length) {
    displayedTitle.value += current[charIndex++]
    isTyping.value = true
    timeout = setTimeout(typeTitle, 80)
  } else {
    isTyping.value = false
    timeout = setTimeout(deleteTitle, 2200)
  }
}

function deleteTitle() {
  if (displayedTitle.value.length > 0) {
    displayedTitle.value = displayedTitle.value.slice(0, -1)
    isTyping.value = true
    timeout = setTimeout(deleteTitle, 40)
  } else {
    titleIndex = (titleIndex + 1) % titles.length
    charIndex = 0
    timeout = setTimeout(typeTitle, 300)
  }
}

onMounted(() => typeTitle())
</script>

<style scoped>
.hero {
  min-height: 100vh;
  display: flex;
  flex-direction: column;
  justify-content: center;
  padding: 120px 0 80px;
  overflow: hidden;
}

.hero-grid {
  position: absolute;
  inset: 0;
  background-image:
    linear-gradient(rgba(99,209,175,0.04) 1px, transparent 1px),
    linear-gradient(90deg, rgba(99,209,175,0.04) 1px, transparent 1px);
  background-size: 60px 60px;
  mask-image: radial-gradient(ellipse 80% 70% at 50% 50%, black, transparent);
}

.orb {
  position: absolute;
  border-radius: 50%;
  filter: blur(80px);
  pointer-events: none;
}
.orb-1 {
  width: 600px; height: 600px;
  background: radial-gradient(circle, rgba(99,209,175,0.12), transparent 70%);
  top: -200px; right: -100px;
}
.orb-2 {
  width: 400px; height: 400px;
  background: radial-gradient(circle, rgba(167,139,250,0.1), transparent 70%);
  bottom: 0; left: -100px;
}

.hero-inner {
  display: grid;
  grid-template-columns: 1fr auto;
  gap: 60px;
  align-items: center;
  position: relative;
  z-index: 1;
}

.hero-badge {
  display: inline-flex;
  align-items: center;
  gap: 8px;
  font-size: 13px;
  font-weight: 500;
  color: var(--accent);
  background: var(--accent-glow);
  border: 1px solid var(--border-accent);
  padding: 7px 14px;
  border-radius: 100px;
  margin-bottom: 24px;
}

.status-dot {
  width: 8px; height: 8px;
  border-radius: 50%;
  background: var(--accent);
  animation: pulse 2s infinite;
}

.hero-title {
  font-family: var(--font-display);
  font-size: clamp(2.2rem, 5vw, 3.8rem);
  font-weight: 800;
  line-height: 1.1;
  margin-bottom: 24px;
  letter-spacing: -0.02em;
}

.name-highlight {
  color: var(--accent);
}

.title-line {
  display: block;
  color: var(--text-muted);
  font-weight: 600;
  margin-top: 8px;
}

.typed-wrapper {
  display: inline-flex;
  align-items: center;
}

.cursor {
  color: var(--accent);
  font-weight: 300;
  margin-left: 2px;
}
.cursor.blink {
  animation: cursorBlink 1s infinite;
}

@keyframes cursorBlink {
  0%, 100% { opacity: 1; }
  50% { opacity: 0; }
}

.hero-desc {
  color: var(--text-muted);
  font-size: 1.05rem;
  max-width: 480px;
  line-height: 1.8;
  margin-bottom: 36px;
}

.hero-actions {
  display: flex;
  gap: 12px;
  flex-wrap: wrap;
  margin-bottom: 48px;
}

.hero-stats {
  display: flex;
  gap: 32px;
  padding-top: 32px;
  border-top: 1px solid var(--border);
}

.stat { display: flex; flex-direction: column; gap: 2px; }

.stat-num {
  font-family: var(--font-display);
  font-size: 1.6rem;
  font-weight: 800;
  color: var(--text);
  line-height: 1;
}

.stat-label {
  font-size: 12px;
  color: var(--text-muted);
  letter-spacing: 0.05em;
}

/* Profile Visual */
.hero-visual {
  position: relative;
  flex-shrink: 0;
}

.profile-frame {
  position: relative;
  width: 320px;
  height: 320px;
}

.profile-rings {
  position: absolute;
  inset: -20px;
}

.ring {
  position: absolute;
  border-radius: 50%;
  border: 1px solid;
  inset: 0;
}

.ring-1 {
  border-color: rgba(99, 209, 175, 0.2);
  animation: spin 20s linear infinite;
}

.ring-2 {
  inset: 15px;
  border-color: rgba(167, 139, 250, 0.15);
  animation: spin 15s linear infinite reverse;
}

@keyframes spin {
  to { transform: rotate(360deg); }
}

.profile-img-wrap {
  width: 100%;
  height: 100%;
  border-radius: 50%;
  overflow: hidden;
  border: 3px solid var(--border-accent);
  background: var(--bg-card);
  box-shadow: 0 0 60px rgba(99, 209, 175, 0.15);
  animation: float 6s ease-in-out infinite;
}

.profile-img {
  width: 100%;
  height: 100%;
  object-fit: cover;
}

.badge-card {
  position: absolute;
  display: flex;
  align-items: center;
  gap: 10px;
  background: var(--bg-card);
  border: 1px solid var(--border);
  border-radius: var(--radius);
  padding: 10px 14px;
  backdrop-filter: blur(12px);
  box-shadow: 0 8px 32px rgba(0,0,0,0.3);
  white-space: nowrap;
  animation: float 6s ease-in-out infinite;
}

.badge-card--tl {
  top: 10%;
  left: -80px;
  animation-delay: -1s;
}

.badge-card--br {
  bottom: 10%;
  right: -70px;
  animation-delay: -3s;
}

.badge-icon { font-size: 1.3rem; }

.badge-title {
  font-family: var(--font-display);
  font-size: 13px;
  font-weight: 700;
  color: var(--text);
}

.badge-sub {
  font-size: 11px;
  color: var(--text-muted);
}

/* Scroll hint */
.scroll-hint {
  position: absolute;
  bottom: 32px;
  left: 50%;
  transform: translateX(-50%);
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 8px;
  color: var(--text-muted);
  font-size: 11px;
  letter-spacing: 0.1em;
  text-transform: uppercase;
  animation: fadeIn 1s 1.5s both;
}

.scroll-mouse {
  width: 22px;
  height: 36px;
  border: 2px solid var(--text-faint);
  border-radius: 11px;
  display: flex;
  justify-content: center;
  padding: 5px;
}

.scroll-wheel {
  width: 3px;
  height: 6px;
  background: var(--accent);
  border-radius: 2px;
  animation: scrollWheel 2s infinite;
}

@keyframes scrollWheel {
  0% { transform: translateY(0); opacity: 1; }
  100% { transform: translateY(10px); opacity: 0; }
}

@media (max-width: 900px) {
  .hero-inner {
    grid-template-columns: 1fr;
    text-align: center;
    gap: 48px;
  }
  .hero-desc { max-width: 100%; }
  .hero-actions { justify-content: center; }
  .hero-stats { justify-content: center; }
  .hero-visual { display: flex; justify-content: center; }
  .badge-card--tl { left: -30px; }
  .badge-card--br { right: -30px; }
}

@media (max-width: 480px) {
  .profile-frame { width: 250px; height: 250px; }
  .badge-card { display: none; }
  .hero-stats { gap: 20px; flex-wrap: wrap; }
  .scroll-hint { display: none; }
}
</style>
