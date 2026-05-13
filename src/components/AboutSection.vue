<template>
  <section id="about" class="about">
    <div class="about__inner">
      <div class="about__image-col">
        <div class="about__image-frame">
          <img
            src="https://images.pexels.com/photos/3760809/pexels-photo-3760809.jpeg?auto=compress&cs=tinysrgb&w=600"
            alt="Professional workspace"
            class="about__photo"
          />
        </div>
        <div class="about__stats">
          <div class="stat">
            <span class="stat__number">10+</span>
            <span class="stat__label">Years Experience</span>
          </div>
          <div class="stat">
            <span class="stat__number">30k+</span>
            <span class="stat__label">Learners Served</span>
          </div>
          <div class="stat">
            <span class="stat__number">USC</span>
            <span class="stat__label">M.S. Summa Cum Laude</span>
          </div>
        </div>
      </div>
      <div class="about__content">
        <p class="section-eyebrow">About Me</p>
        <h2 class="section-title">Clarity is a craft.</h2>
        <p class="about__text">
          I'm a technical writer and instructional designer with 10+ years turning complex
          information into clear, structured learning experiences. My work spans SaaS product
          documentation, interactive e-learning, curriculum design, and instructional video —
          always with the end user in mind.
        </p>
        <p class="about__text">
          I've written for learners at Google, Intel, and Nucor Steel, led LMS migrations
          serving 30,000+ users, and currently own end-to-end documentation at Resolve Systems
          using a docs-as-code workflow. I hold an M.S. in Educational Psychology &amp;
          Instructional Technology from USC, Summa Cum Laude.
        </p>
        <div class="about__expertise">
          <div class="expertise-item">
            <div class="expertise-icon">
              <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.8"><path d="M12 6.253v13m0-13C10.832 5.477 9.246 5 7.5 5S4.168 5.477 3 6.253v13C4.168 18.477 5.754 18 7.5 18s3.332.477 4.5 1.253m0-13C13.168 5.477 14.754 5 16.5 5c1.747 0 3.332.477 4.5 1.253v13C19.832 18.477 18.247 18 16.5 18c-1.746 0-3.332.477-4.5 1.253"/></svg>
            </div>
            <div>
              <h4>Technical Writing</h4>
              <p>SaaS product docs, release notes, user guides, and docs-as-code workflows (Docusaurus, GitHub)</p>
            </div>
          </div>
          <div class="expertise-item">
            <div class="expertise-icon">
              <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.8"><path d="M9.75 17L9 20l-1 1h8l-1-1-.75-3M3 13h18M5 17h14a2 2 0 002-2V5a2 2 0 00-2-2H5a2 2 0 00-2 2v10a2 2 0 002 2z"/></svg>
            </div>
            <div>
              <h4>Instructional Design</h4>
              <p>E-learning in Articulate Storyline &amp; Rise, curriculum architecture, LMS administration, SCORM/xAPI</p>
            </div>
          </div>
          <div class="expertise-item">
            <div class="expertise-icon">
              <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.8"><polygon points="23 7 16 12 23 17 23 7"/><rect x="1" y="5" width="15" height="14" rx="2" ry="2"/></svg>
            </div>
            <div>
              <h4>Video & Multimedia</h4>
              <p>Screen recording with Camtasia, AI voiceover via ElevenLabs, and Descript-based editing</p>
            </div>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<style scoped>
.about {
  padding: var(--space-16) var(--space-4);
  background: white;
}

.about__inner {
  max-width: 1200px;
  margin: 0 auto;
  display: grid;
  grid-template-columns: 1fr 1.4fr;
  gap: var(--space-12);
  align-items: start;
}

.about__image-col {
  display: flex;
  flex-direction: column;
  gap: var(--space-4);
}

.about__image-frame {
  border-radius: 16px;
  overflow: hidden;
  aspect-ratio: 4/5;
  box-shadow: 0 20px 60px rgba(30, 95, 116, 0.15);
}

.about__photo {
  width: 100%;
  height: 100%;
  object-fit: cover;
  transition: transform 0.4s ease;
}

.about__image-frame:hover .about__photo {
  transform: scale(1.03);
}

.about__stats {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: var(--space-2);
}

.stat {
  text-align: center;
  padding: var(--space-2);
  background: var(--color-neutral-50);
  border-radius: 10px;
}

.stat__number {
  display: block;
  font-family: var(--font-display);
  font-size: 1.5rem;
  font-weight: 600;
  color: var(--color-primary);
}

.stat__label {
  display: block;
  font-size: 0.72rem;
  font-weight: 500;
  color: var(--color-neutral-500);
  text-transform: uppercase;
  letter-spacing: 0.05em;
  margin-top: 2px;
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
  font-size: clamp(1.8rem, 4vw, 2.8rem);
  color: var(--color-neutral-900);
  margin-bottom: var(--space-3);
}

.about__text {
  font-size: 1rem;
  color: var(--color-neutral-600);
  line-height: 1.8;
  margin-bottom: var(--space-3);
}

.about__expertise {
  display: flex;
  flex-direction: column;
  gap: var(--space-3);
  margin-top: var(--space-4);
}

.expertise-item {
  display: flex;
  gap: var(--space-2);
  align-items: flex-start;
}

.expertise-icon {
  flex-shrink: 0;
  width: 40px;
  height: 40px;
  background: rgba(30, 95, 116, 0.08);
  border-radius: 10px;
  display: flex;
  align-items: center;
  justify-content: center;
  color: var(--color-primary);
}

.expertise-icon svg {
  width: 20px;
  height: 20px;
}

.expertise-item h4 {
  font-size: 0.95rem;
  font-weight: 600;
  color: var(--color-neutral-800);
  margin-bottom: 2px;
}

.expertise-item p {
  font-size: 0.875rem;
  color: var(--color-neutral-500);
  line-height: 1.5;
}

@media (max-width: 900px) {
  .about__inner {
    grid-template-columns: 1fr;
  }
  .about__image-frame {
    aspect-ratio: 16/9;
  }
}
</style>
