<template>
  <article :class="['card', { 'card--gallery': item.isSlideGallery }]">
    <div v-if="item.images && item.images.length" class="card__slide-grid">
      <div
        v-for="(src, i) in item.images"
        :key="i"
        class="card__slide-cell"
        @click="lightboxIndex = i; lightboxOpen = true"
      >
        <img :src="src" :alt="item.title + ' slide ' + (i + 1)" />
      </div>
      <div class="card__overlay">
        <span class="card__type">{{ item.type }}</span>
      </div>
    </div>
    <div v-else class="card__image-wrap">
      <img :src="item.image" :alt="item.title" class="card__image" />
      <div class="card__overlay">
        <span class="card__type">{{ item.type }}</span>
      </div>
    </div>

    <Teleport to="body">
      <div v-if="lightboxOpen" class="lightbox" @click.self="lightboxOpen = false">
        <button class="lightbox__close" @click="lightboxOpen = false">&#x2715;</button>
        <button class="lightbox__prev" @click="lightboxIndex = (lightboxIndex - 1 + item.images.length) % item.images.length">&#8592;</button>
        <img :src="item.images[lightboxIndex]" :alt="item.title + ' slide ' + (lightboxIndex + 1)" class="lightbox__img" />
        <button class="lightbox__next" @click="lightboxIndex = (lightboxIndex + 1) % item.images.length">&#8594;</button>
        <span class="lightbox__counter">{{ lightboxIndex + 1 }} / {{ item.images.length }}</span>
      </div>
    </Teleport>
    <div class="card__body">
      <h3 class="card__title">{{ item.title }}</h3>
      <p class="card__desc">{{ item.description }}</p>
      <div class="card__tags">
        <span v-for="tag in item.tags" :key="tag" class="tag">{{ tag }}</span>
      </div>
      <div class="card__footer">
        <span v-if="item.note" class="card__note">{{ item.note }}</span>
        <a
          v-if="item.link"
          :href="item.link"
          target="_blank"
          rel="noopener"
          class="card__link"
        >
          {{ item.linkLabel }}
          <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><path d="M18 13v6a2 2 0 01-2 2H5a2 2 0 01-2-2V8a2 2 0 012-2h6M15 3h6v6M10 14L21 3"/></svg>
        </a>
        <span v-else-if="item.linkLabel" class="card__link card__link--muted">
          {{ item.linkLabel }}
          <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><path d="M12 15v2m-6 4h12a2 2 0 002-2v-6a2 2 0 00-2-2H6a2 2 0 00-2 2v6a2 2 0 002 2zm10-10V7a4 4 0 00-8 0v4h8z"/></svg>
        </span>
      </div>
    </div>
  </article>
</template>

<script setup>
import { ref } from 'vue'
defineProps({ item: Object })
const lightboxOpen = ref(false)
const lightboxIndex = ref(0)
</script>

<style scoped>
.card {
  background: white;
  border-radius: 14px;
  overflow: hidden;
  box-shadow: 0 2px 12px rgba(0, 0, 0, 0.06);
  transition: transform 0.25s ease, box-shadow 0.25s ease;
  display: flex;
  flex-direction: column;
}

.card:hover {
  transform: translateY(-4px);
  box-shadow: 0 12px 40px rgba(30, 95, 116, 0.14);
}

.card__slide-grid {
  position: relative;
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 3px;
  background: var(--color-neutral-200);
}

.card__slide-cell {
  overflow: hidden;
  cursor: zoom-in;
  aspect-ratio: 16/10;
}

.card__slide-cell img {
  width: 100%;
  height: 100%;
  object-fit: cover;
  transition: transform 0.3s ease;
}

.card__slide-cell:hover img {
  transform: scale(1.06);
}

.lightbox {
  position: fixed;
  inset: 0;
  z-index: 1000;
  background: rgba(0, 0, 0, 0.92);
  display: flex;
  align-items: center;
  justify-content: center;
}

.lightbox__img {
  max-width: 90vw;
  max-height: 85vh;
  object-fit: contain;
  border-radius: 4px;
  box-shadow: 0 24px 80px rgba(0,0,0,0.6);
}

.lightbox__close {
  position: absolute;
  top: 20px;
  right: 24px;
  background: none;
  border: none;
  color: white;
  font-size: 1.5rem;
  cursor: pointer;
  opacity: 0.7;
  transition: opacity 0.2s;
}

.lightbox__close:hover { opacity: 1; }

.lightbox__prev,
.lightbox__next {
  position: absolute;
  top: 50%;
  transform: translateY(-50%);
  background: rgba(255,255,255,0.12);
  border: none;
  color: white;
  font-size: 1.6rem;
  padding: 12px 18px;
  cursor: pointer;
  border-radius: 8px;
  transition: background 0.2s;
}

.lightbox__prev:hover,
.lightbox__next:hover { background: rgba(255,255,255,0.25); }

.lightbox__prev { left: 20px; }
.lightbox__next { right: 20px; }

.lightbox__counter {
  position: absolute;
  bottom: 20px;
  left: 50%;
  transform: translateX(-50%);
  color: rgba(255,255,255,0.6);
  font-size: 0.85rem;
}

.card__image-wrap {
  position: relative;
  aspect-ratio: 16/9;
  overflow: hidden;
}

.card__image {
  width: 100%;
  height: 100%;
  object-fit: cover;
  transition: transform 0.4s ease;
}

.card:hover .card__image {
  transform: scale(1.04);
}

.card__overlay {
  position: absolute;
  top: var(--space-2);
  left: var(--space-2);
}

.card__type {
  background: rgba(0, 0, 0, 0.55);
  backdrop-filter: blur(4px);
  color: white;
  font-size: 0.7rem;
  font-weight: 600;
  letter-spacing: 0.06em;
  text-transform: uppercase;
  padding: 4px 10px;
  border-radius: 100px;
}

.card__body {
  padding: var(--space-3);
  display: flex;
  flex-direction: column;
  flex: 1;
}

.card__title {
  font-family: var(--font-display);
  font-size: 1.15rem;
  color: var(--color-neutral-900);
  margin-bottom: 8px;
}

.card__desc {
  font-size: 0.875rem;
  color: var(--color-neutral-500);
  line-height: 1.65;
  flex: 1;
  margin-bottom: var(--space-2);
}

.card__tags {
  display: flex;
  flex-wrap: wrap;
  gap: 6px;
  margin-bottom: var(--space-2);
}

.tag {
  font-size: 0.7rem;
  font-weight: 500;
  padding: 3px 10px;
  border-radius: 100px;
  background: rgba(30, 95, 116, 0.08);
  color: var(--color-primary);
}

.card__footer {
  display: flex;
  align-items: center;
  justify-content: space-between;
  padding-top: var(--space-2);
  border-top: 1px solid var(--color-neutral-100);
  gap: var(--space-2);
  flex-wrap: wrap;
}

.card__note {
  font-size: 0.78rem;
  color: var(--color-neutral-400);
  font-style: italic;
}

.card__link {
  display: inline-flex;
  align-items: center;
  gap: 5px;
  font-size: 0.82rem;
  font-weight: 600;
  color: var(--color-primary);
  text-decoration: none;
  transition: color 0.2s;
  margin-left: auto;
  white-space: nowrap;
}

.card__link:hover {
  color: var(--color-primary-light);
}

.card__link--muted {
  color: var(--color-neutral-400);
  cursor: default;
}

.card__link svg {
  width: 13px;
  height: 13px;
}
</style>
