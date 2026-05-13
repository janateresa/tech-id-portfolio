<template>
  <section id="contact" class="contact">
    <div class="contact__inner">
      <div class="contact__content">
        <p class="section-eyebrow">Contact</p>
        <h2 class="section-title">Let's work together.</h2>
        <p class="contact__text">
          Looking for a technical writer or instructional designer for your next project?
          I'd love to hear about what you're building.
        </p>
        <a href="mailto:js@jsosnowski.com" class="contact__email">
          <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.8"><path d="M3 8l7.89 5.26a2 2 0 002.22 0L21 8M5 19h14a2 2 0 002-2V7a2 2 0 00-2-2H5a2 2 0 00-2 2v10a2 2 0 002 2z"/></svg>
          js@jsosnowski.com
        </a>
      </div>
      <div class="contact__visual">
        <div class="contact__badge">
          <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.5" class="badge-icon"><path d="M20 21v-2a4 4 0 00-4-4H8a4 4 0 00-4 4v2"/><circle cx="12" cy="7" r="4"/></svg>
          <span>Available for freelance</span>
        </div>
        <div class="contact__services">
          <div class="service-chip" v-for="s in services" :key="s">{{ s }}</div>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup>
const services = [
  'SaaS Product Documentation',
  'E-Learning Development',
  'Curriculum Architecture',
  'Docs-as-Code (Docusaurus)',
  'Instructional Video',
  'LMS Administration',
  'Job Aids & Quick Guides',
  'SME Collaboration',
]
</script>

<style scoped>
.contact {
  padding: var(--space-16) var(--space-4);
  background: white;
}

.contact__inner {
  max-width: 1100px;
  margin: 0 auto;
  display: grid;
  grid-template-columns: 1.1fr 1fr;
  gap: var(--space-12);
  align-items: center;
}

.section-eyebrow {
  font-size: 0.78rem;
  font-weight: 600;
  letter-spacing: 0.14em;
  text-transform: uppercase;
  color: var(--color-accent);
  margin-bottom: var(--space-2);
}

.section-title {
  font-family: var(--font-display);
  font-size: clamp(2rem, 5vw, 3rem);
  color: var(--color-neutral-900);
  margin-bottom: var(--space-3);
}

.contact__text {
  font-size: 1rem;
  color: var(--color-neutral-600);
  line-height: 1.8;
  max-width: 440px;
  margin-bottom: var(--space-4);
}

.contact__email {
  display: inline-flex;
  align-items: center;
  gap: 10px;
  font-size: 1.15rem;
  font-weight: 600;
  color: var(--color-primary);
  text-decoration: none;
  border-bottom: 2px solid transparent;
  padding-bottom: 2px;
  transition: border-color 0.2s, color 0.2s;
}

.contact__email:hover {
  color: var(--color-primary-light);
  border-color: var(--color-primary-light);
}

.contact__email svg {
  width: 22px;
  height: 22px;
}

.contact__note {
  font-size: 0.75rem;
  color: var(--color-neutral-400);
  margin-top: var(--space-1);
  font-style: italic;
}

.contact__visual {
  display: flex;
  flex-direction: column;
  gap: var(--space-4);
}

.contact__badge {
  display: inline-flex;
  align-items: center;
  gap: 10px;
  background: rgba(46, 125, 82, 0.1);
  border: 1.5px solid rgba(46, 125, 82, 0.25);
  color: var(--color-success);
  padding: 10px 20px;
  border-radius: 100px;
  font-size: 0.9rem;
  font-weight: 600;
  align-self: flex-start;
}

.badge-icon {
  width: 18px;
  height: 18px;
}

.contact__services {
  display: flex;
  flex-wrap: wrap;
  gap: var(--space-1);
}

.service-chip {
  padding: 7px 14px;
  background: var(--color-neutral-50);
  border: 1.5px solid var(--color-neutral-200);
  border-radius: 8px;
  font-size: 0.82rem;
  font-weight: 500;
  color: var(--color-neutral-600);
}

@media (max-width: 768px) {
  .contact__inner {
    grid-template-columns: 1fr;
  }
}
</style>
