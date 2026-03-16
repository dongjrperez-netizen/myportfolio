<template>
  <footer class="footer">
    <div class="container footer-inner">
      <div class="footer-top">
        <div class="footer-brand">
          <a href="#home" class="logo">
            <span class="logo-bracket">&lt;</span>AR<span class="logo-bracket">/&gt;</span>
          </a>
          <p class="footer-tagline">Building the web, one component at a time.</p>
        </div>
        <div class="footer-nav">
          <a v-for="link in navLinks" :key="link" :href="`#${link.toLowerCase()}`" class="footer-link">{{ link }}</a>
        </div>
      </div>
      <div class="footer-bottom">
        <p class="copyright">© {{ year }} Roger Perez. Crafted with Vue.js ❤️</p>
        <button class="back-top" @click="scrollTop">
          <svg width="16" height="16" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.5">
            <path d="M18 15l-6-6-6 6"/>
          </svg>
          Back to top
        </button>
      </div>
    </div>
  </footer>
</template>

<script setup>
const year = new Date().getFullYear()
const navLinks = ['Home', 'About', 'Skills', 'Projects', 'Contact']
const scrollTop = () => window.scrollTo({ top: 0, behavior: 'smooth' })
</script>

<style scoped>
.footer {
  background: var(--bg-2);
  border-top: 1px solid var(--border);
  padding: 48px 0 32px;
}

.footer-top {
  display: flex;
  align-items: center;
  justify-content: space-between;
  gap: 32px;
  margin-bottom: 32px;
  padding-bottom: 32px;
  border-bottom: 1px solid var(--border);
  flex-wrap: wrap;
}

.logo {
  font-family: var(--font-display);
  font-weight: 800;
  font-size: 1.2rem;
  color: var(--text);
  display: block;
  margin-bottom: 8px;
}
.logo-bracket { color: var(--accent); }

.footer-tagline {
  font-size: 13px;
  color: var(--text-muted);
}

.footer-nav {
  display: flex;
  gap: 4px;
  flex-wrap: wrap;
}

.footer-link {
  font-size: 14px;
  color: var(--text-muted);
  padding: 6px 12px;
  border-radius: 8px;
  transition: var(--transition);
}

.footer-link:hover {
  color: var(--accent);
  background: var(--accent-glow);
}

.footer-bottom {
  display: flex;
  align-items: center;
  justify-content: space-between;
  flex-wrap: wrap;
  gap: 16px;
}

.copyright {
  font-size: 13px;
  color: var(--text-muted);
}

.back-top {
  display: inline-flex;
  align-items: center;
  gap: 6px;
  font-size: 13px;
  font-family: var(--font-display);
  font-weight: 600;
  color: var(--text-muted);
  background: var(--bg-card);
  border: 1px solid var(--border);
  padding: 8px 16px;
  border-radius: 8px;
  transition: var(--transition);
}

.back-top:hover {
  color: var(--accent);
  border-color: var(--border-accent);
  transform: translateY(-2px);
}
</style>
