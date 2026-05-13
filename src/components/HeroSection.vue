<template>
  <section id="home" class="hero">
    <div class="hero__bg"></div>
    <div class="hero__inner">
      <p class="hero__eyebrow">Portfolio</p>
      <h1 class="hero__name">Jana Sosnowski</h1>
      <p class="hero__title">Technical Writer <span class="hero__divider">&amp;</span> Instructional Designer</p>
      <p class="hero__tagline">
        USC-trained. Google, Intel, and enterprise-tested. Turning complex information
        into clear documentation and engaging learning experiences for 10+ years.
      </p>
      <div class="hero__actions">
        <a href="#work" class="btn btn--primary">View My Work</a>
        <a href="#contact" class="btn btn--outline">Get in Touch</a>
      </div>
    </div>
    <div class="hero__scroll-hint">
      <span>Scroll to explore</span>
      <div class="hero__scroll-line"></div>
    </div>
  </section>
</template>

<style scoped>
.hero {
  position: relative;
  min-height: 100vh;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  overflow: hidden;
  background: linear-gradient(160deg, #0f3d52 0%, #1e5f74 45%, #2d7d96 100%);
}

.hero__bg {
  position: absolute;
  inset: 0;
  background-image:
    radial-gradient(ellipse at 20% 50%, rgba(45, 139, 165, 0.3) 0%, transparent 60%),
    radial-gradient(ellipse at 80% 20%, rgba(200, 121, 65, 0.15) 0%, transparent 50%);
  pointer-events: none;
}

.hero__inner {
  position: relative;
  z-index: 1;
  max-width: 760px;
  padding: var(--space-4);
  text-align: center;
}

.hero__eyebrow {
  font-size: 0.8rem;
  font-weight: 600;
  letter-spacing: 0.15em;
  text-transform: uppercase;
  color: rgba(255,255,255,0.6);
  margin-bottom: var(--space-2);
}

.hero__name {
  font-family: var(--font-display);
  font-size: clamp(3rem, 8vw, 5.5rem);
  font-weight: 600;
  color: white;
  letter-spacing: -0.02em;
  margin-bottom: var(--space-2);
}

.hero__title {
  font-size: clamp(1.1rem, 3vw, 1.5rem);
  font-weight: 300;
  color: rgba(255, 255, 255, 0.85);
  letter-spacing: 0.04em;
  margin-bottom: var(--space-3);
}

.hero__divider {
  color: var(--color-accent-light);
  font-weight: 500;
}

.hero__tagline {
  font-size: 1.05rem;
  color: rgba(255, 255, 255, 0.7);
  line-height: 1.7;
  max-width: 560px;
  margin: 0 auto var(--space-5);
}

.hero__actions {
  display: flex;
  gap: var(--space-2);
  justify-content: center;
  flex-wrap: wrap;
}

.btn {
  display: inline-block;
  padding: 14px 32px;
  border-radius: 8px;
  font-size: 0.95rem;
  font-weight: 600;
  letter-spacing: 0.02em;
  transition: all 0.2s ease;
  text-decoration: none;
}

.btn--primary {
  background: var(--color-accent);
  color: white;
  border: 2px solid var(--color-accent);
}

.btn--primary:hover {
  background: var(--color-accent-light);
  border-color: var(--color-accent-light);
  color: white;
  transform: translateY(-1px);
}

.btn--outline {
  background: transparent;
  color: white;
  border: 2px solid rgba(255, 255, 255, 0.5);
}

.btn--outline:hover {
  border-color: white;
  background: rgba(255, 255, 255, 0.1);
  color: white;
  transform: translateY(-1px);
}

.hero__scroll-hint {
  position: absolute;
  bottom: var(--space-4);
  left: 50%;
  transform: translateX(-50%);
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 8px;
  color: rgba(255, 255, 255, 0.4);
  font-size: 0.7rem;
  letter-spacing: 0.12em;
  text-transform: uppercase;
}

.hero__scroll-line {
  width: 1px;
  height: 40px;
  background: linear-gradient(to bottom, rgba(255,255,255,0.4), transparent);
  animation: scrollPulse 2s ease-in-out infinite;
}

@keyframes scrollPulse {
  0%, 100% { opacity: 0.3; transform: scaleY(1); }
  50% { opacity: 0.8; transform: scaleY(1.1); }
}
</style>
