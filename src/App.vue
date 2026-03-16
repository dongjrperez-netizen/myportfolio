<template>
  <div id="app-root">
    <Navbar :active-section="activeSection" />
    <main>
      <Hero />
      <About />
      <Skills />
      <Projects />
      <Contact />
    </main>
    <Footer />
  </div>
</template>

<script setup>
import { ref, onMounted, onUnmounted } from 'vue'
import Navbar from './components/Navbar.vue'
import Hero from './components/Hero.vue'
import About from './components/About.vue'
import Skills from './components/Skills.vue'
import Projects from './components/Projects.vue'
import Contact from './components/Contact.vue'
import Footer from './components/Footer.vue'

const activeSection = ref('home')

const handleScroll = () => {
  const sections = ['home', 'about', 'skills', 'projects', 'contact']
  const scrollY = window.scrollY + 100

  for (const id of sections) {
    const el = document.getElementById(id)
    if (el) {
      const top = el.offsetTop
      const bottom = top + el.offsetHeight
      if (scrollY >= top && scrollY < bottom) {
        activeSection.value = id
        break
      }
    }
  }
}

onMounted(() => window.addEventListener('scroll', handleScroll, { passive: true }))
onUnmounted(() => window.removeEventListener('scroll', handleScroll))
</script>

<style>
#app-root {
  min-height: 100vh;
  display: flex;
  flex-direction: column;
}
main { flex: 1; }
</style>
