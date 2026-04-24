<template>
  <header :class="['navbar', { scrolled: isScrolled, 'menu-open': menuOpen }]">
    <div class="container nav-inner">
      <a href="#home" class="logo" @click="menuOpen = false">
        <span class="logo-bracket">&lt;</span>
        Roger C. Perez Jr.
        <span class="logo-bracket">/&gt;</span>
      </a>

      <nav class="nav-links" :class="{ open: menuOpen }">
        <a
          v-for="item in navItems"
          :key="item.id"
          :href="`#${item.id}`"
          :class="['nav-link', { active: activeSection === item.id }]"
          @click="menuOpen = false"
        >
          {{ item.label }}
        </a>
        <a href="#" class="btn btn-primary btn-sm nav-cta" @click.prevent="downloadCV">
          <svg width="14" height="14" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.5">
            <path d="M21 15v4a2 2 0 01-2 2H5a2 2 0 01-2-2v-4M7 10l5 5 5-5M12 15V3"/>
          </svg>
          Download CV
        </a>
      </nav>

      <button class="hamburger" @click="menuOpen = !menuOpen" :aria-expanded="menuOpen" aria-label="Toggle menu">
        <span></span>
        <span></span>
        <span></span>
      </button>
    </div>
  </header>
</template>

<script setup>
import { ref, onMounted, onUnmounted } from 'vue'

const props = defineProps({ activeSection: String })
const isScrolled = ref(false)
const menuOpen = ref(false)

const navItems = [
  { id: 'home', label: 'Home' },
  { id: 'about', label: 'About' },
  { id: 'skills', label: 'Skills' },
  { id: 'projects', label: 'Projects' },
  { id: 'contact', label: 'Contact' },
]

const handleScroll = () => { isScrolled.value = window.scrollY > 30 }

const downloadCV = () => {
  const link = document.createElement('a')
  link.href = '/myCV/My Resume roger.pdf'
  link.download = 'Roger_Resume.pdf'
  link.click()
}

onMounted(() => window.addEventListener('scroll', handleScroll, { passive: true }))
onUnmounted(() => window.removeEventListener('scroll', handleScroll))
</script>

<style scoped>
.navbar {
  position: fixed;
  top: 0;
  left: 0;
  right: 0;
  z-index: 1000;
  padding: 20px 0;
  transition: var(--transition);
}

.navbar.scrolled {
  padding: 14px 0;
  background: rgba(10, 10, 15, 0.9);
  backdrop-filter: blur(20px);
  -webkit-backdrop-filter: blur(20px);
  border-bottom: 1px solid var(--border);
}

.nav-inner {
  display: flex;
  align-items: center;
  justify-content: space-between;
  gap: 32px;
}

.logo {
  font-family: var(--font-display);
  font-weight: 800;
  font-size: 1.2rem;
  color: var(--text);
  letter-spacing: 0.05em;
  flex-shrink: 0;
}

.logo-bracket {
  color: var(--accent);
}

.nav-links {
  display: flex;
  align-items: center;
  gap: 8px;
}

.nav-link {
  font-family: var(--font-display);
  font-size: 14px;
  font-weight: 500;
  color: var(--text-muted);
  padding: 8px 14px;
  border-radius: 8px;
  transition: var(--transition);
  position: relative;
}

.nav-link::after {
  content: '';
  position: absolute;
  bottom: 4px;
  left: 50%;
  transform: translateX(-50%);
  width: 0;
  height: 2px;
  background: var(--accent);
  border-radius: 1px;
  transition: var(--transition);
}

.nav-link:hover,
.nav-link.active {
  color: var(--text);
}

.nav-link.active::after {
  width: 20px;
}

.nav-cta {
  margin-left: 8px;
}

.hamburger {
  display: none;
  flex-direction: column;
  gap: 5px;
  padding: 8px;
  background: transparent;
  border-radius: 8px;
  border: 1px solid var(--border);
}

.hamburger span {
  display: block;
  width: 22px;
  height: 2px;
  background: var(--text);
  border-radius: 1px;
  transition: var(--transition);
}

.menu-open .hamburger span:nth-child(1) {
  transform: translateY(7px) rotate(45deg);
}
.menu-open .hamburger span:nth-child(2) {
  opacity: 0;
}
.menu-open .hamburger span:nth-child(3) {
  transform: translateY(-7px) rotate(-45deg);
}

@media (max-width: 768px) {
  .hamburger { display: flex; }

  .nav-links {
    position: fixed;
    top: 0;
    right: -100%;
    bottom: 0;
    width: 280px;
    flex-direction: column;
    align-items: flex-start;
    justify-content: center;
    gap: 4px;
    padding: 40px 32px;
    background: var(--bg-2);
    border-left: 1px solid var(--border);
    transition: right 0.3s cubic-bezier(0.4, 0, 0.2, 1);
  }

  .nav-links.open {
    right: 0;
  }

  .nav-link {
    font-size: 1.1rem;
    padding: 12px 0;
    width: 100%;
    border-radius: 0;
    border-bottom: 1px solid var(--border);
  }

  .nav-cta {
    margin-left: 0;
    margin-top: 16px;
    width: 100%;
    justify-content: center;
  }
}
</style>
