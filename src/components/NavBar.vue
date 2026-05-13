<template>
  <header :class="['navbar', { scrolled: isScrolled }]">
    <div class="navbar__inner">
      <a href="#home" class="navbar__logo">Jana Sosnowski</a>
      <nav class="navbar__nav">
        <a href="#about">About</a>
        <a href="#work">Work</a>
        <a href="#tools">Skills</a>
        <a href="#contact" class="navbar__cta">Get in Touch</a>
      </nav>
      <button class="navbar__hamburger" @click="menuOpen = !menuOpen" :aria-expanded="menuOpen">
        <span></span><span></span><span></span>
      </button>
    </div>
    <div :class="['navbar__mobile', { open: menuOpen }]" @click="menuOpen = false">
      <a href="#about">About</a>
      <a href="#work">Work</a>
      <a href="#tools">Skills</a>
      <a href="#contact">Get in Touch</a>
    </div>
  </header>
</template>

<script setup>
import { ref, onMounted, onUnmounted } from 'vue'

const isScrolled = ref(false)
const menuOpen = ref(false)

function handleScroll() {
  isScrolled.value = window.scrollY > 40
}

onMounted(() => window.addEventListener('scroll', handleScroll))
onUnmounted(() => window.removeEventListener('scroll', handleScroll))
</script>

<style scoped>
.navbar {
  position: fixed;
  top: 0;
  left: 0;
  right: 0;
  z-index: 100;
  padding: 20px 0;
  transition: background 0.3s ease, box-shadow 0.3s ease, padding 0.3s ease;
}

.navbar.scrolled {
  background: rgba(255, 255, 255, 0.97);
  box-shadow: 0 1px 20px rgba(0, 0, 0, 0.08);
  padding: 14px 0;
}

.navbar__inner {
  max-width: 1200px;
  margin: 0 auto;
  padding: 0 var(--space-4);
  display: flex;
  align-items: center;
  justify-content: space-between;
}

.navbar__logo {
  font-family: var(--font-display);
  font-size: 1.25rem;
  font-weight: 600;
  color: var(--color-primary);
  letter-spacing: -0.01em;
  text-decoration: none;
  transition: color 0.2s;
}

.navbar__logo:hover {
  color: var(--color-primary-light);
}

.navbar__nav {
  display: flex;
  align-items: center;
  gap: var(--space-4);
}

.navbar__nav a {
  font-size: 0.9rem;
  font-weight: 500;
  color: var(--color-neutral-700);
  text-decoration: none;
  letter-spacing: 0.01em;
  transition: color 0.2s;
}

.navbar__nav a:hover {
  color: var(--color-primary);
}

.navbar__cta {
  background: var(--color-primary);
  color: white !important;
  padding: 8px 20px;
  border-radius: 6px;
  transition: background 0.2s !important;
}

.navbar__cta:hover {
  background: var(--color-primary-dark);
  color: white !important;
}

.navbar__hamburger {
  display: none;
  flex-direction: column;
  gap: 5px;
  background: none;
  border: none;
  padding: 4px;
}

.navbar__hamburger span {
  display: block;
  width: 22px;
  height: 2px;
  background: var(--color-neutral-700);
  border-radius: 2px;
  transition: background 0.2s;
}

.navbar__mobile {
  display: none;
  flex-direction: column;
  gap: var(--space-2);
  background: white;
  padding: var(--space-3) var(--space-4);
  border-top: 1px solid var(--color-neutral-100);
  max-height: 0;
  overflow: hidden;
  transition: max-height 0.3s ease;
}

.navbar__mobile.open {
  max-height: 300px;
}

.navbar__mobile a {
  font-size: 1rem;
  font-weight: 500;
  color: var(--color-neutral-700);
  text-decoration: none;
  padding: 8px 0;
}

@media (max-width: 768px) {
  .navbar__nav {
    display: none;
  }
  .navbar__hamburger {
    display: flex;
  }
  .navbar__mobile {
    display: flex;
  }
}
</style>
