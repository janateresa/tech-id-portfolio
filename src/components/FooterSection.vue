<template>
  <footer class="footer">
    <div class="footer__inner">
      <p class="footer__name">Jana Sosnowski</p>
      <p class="footer__tagline">Technical Writer &amp; Instructional Designer</p>
      <p class="footer__copy">&copy; {{ year }} Jana Sosnowski. All rights reserved.</p>
    </div>
  </footer>
</template>

<script setup>
const year = new Date().getFullYear()
</script>

<style scoped>
.footer {
  background: var(--color-neutral-900);
  padding: var(--space-6) var(--space-4);
}

.footer__inner {
  max-width: 1200px;
  margin: 0 auto;
  text-align: center;
}

.footer__name {
  font-family: var(--font-display);
  font-size: 1.1rem;
  color: white;
  margin-bottom: 4px;
}

.footer__tagline {
  font-size: 0.85rem;
  color: rgba(255, 255, 255, 0.4);
  margin-bottom: var(--space-3);
}

.footer__copy {
  font-size: 0.78rem;
  color: rgba(255, 255, 255, 0.25);
}
</style>
