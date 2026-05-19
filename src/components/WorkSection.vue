<template>
  <section id="work" class="work">
    <div class="work__inner">
      <div class="work__header">
        <p class="section-eyebrow">Portfolio</p>
        <h2 class="section-title">Selected Work</h2>
        <p class="work__subtitle">
          A selection of projects spanning e-learning design, product documentation, and instructional video.
        </p>
      </div>

      <div class="work__filters">
        <button
          v-for="cat in categories"
          :key="cat.id"
          :class="['filter-btn', { active: activeCategory === cat.id }]"
          @click="activeCategory = cat.id"
        >
          {{ cat.label }}
        </button>
      </div>

      <div class="work__grid">
        <template v-for="item in filteredItems" :key="item.id">
          <WorkCard :item="item" />
        </template>
      </div>
    </div>
  </section>
</template>

<script setup>
import { ref, computed } from 'vue'
import WorkCard from './WorkCard.vue'

const activeCategory = ref('all')

const categories = [
  { id: 'all', label: 'All Work' },
  { id: 'elearning', label: 'E-Learning' },
  { id: 'video', label: 'Video' },
  { id: 'docs', label: 'Documentation' },
  { id: 'slides', label: 'Slide Design' },
]

const items = [
  {
    id: 11,
    category: 'elearning',
    title: 'Grow with Google — Foundations: Data, Data, Everywhere',
    type: 'Script & Reading Authoring · Coursera / Google Career Certificates',
    description: 'Wrote multiple scripts and readings for this course in the Grow with Google Cloud Data Analytics certification series, published on Coursera. The course covers data analytics fundamentals across four modules — analytical thinking, data concepts, toolbox setup, and data ethics — and has been viewed by over 16 million learners globally. Collaborated with Google SMEs and instructional designers to ensure technical accuracy and learning impact.',
    tags: ['Google', 'Coursera', 'Script Writing', 'Data Analytics', 'SME Collaboration'],
    image: 'https://images.pexels.com/photos/546819/pexels-photo-546819.jpeg?auto=compress&cs=tinysrgb&w=800',
    link: 'https://www.coursera.org/learn/foundations-data',
    linkLabel: 'View Course',
    note: null,
    featured: true,
  },
  {
    id: 10,
    category: 'elearning',
    title: 'Intel® Telco Cloud Academy — Infra Management Technologies',
    type: 'Script & Slide Authoring · Intel® Network Builders',
    description: 'Wrote scripts and created slides for four courses within Intel\'s 11-module Telco Cloud Academy certification series: Course 1 (Intro to Ethernet Controllers), Course 3 (QuickAssist Technology / QAT), Course 6 (Open Virtual Switching / OvS), and Course 9 (Data Plane Development Kit / DPDK 101). Collaborated with Intel SMEs to translate highly technical networking content into clear, structured instructional writing for a global developer audience.',
    tags: ['Intel', 'Script Writing', 'Telco Cloud', 'DPDK', 'OvS', 'QAT', 'SME Collaboration'],
    image: 'https://images.pexels.com/photos/546819/pexels-photo-546819.jpeg?auto=compress&cs=tinysrgb&w=800',
    link: 'https://builders.intel.com/university/coursescategory/intel-telco-cloud-academy/introduction-to-intel-infrastructure-management-technologies/courseslist/jd',
    linkLabel: 'View Course',
    note: null,
    featured: true,
  },
  {
    id: 1,
    category: 'elearning',
    title: 'Introduction to Becoming an HHA',
    type: 'Articulate Rise Course',
    description: 'A full onboarding course for Home Health Aide candidates, built entirely in Articulate Rise using the client\'s branding. Combines structured learning paths with interactive assessments.',
    tags: ['Articulate Rise', 'Healthcare', 'Onboarding'],
    image: 'https://images.pexels.com/photos/1181671/pexels-photo-1181671.jpeg?auto=compress&cs=tinysrgb&w=800',
    link: 'https://360.articulate.com/review/content/e16f4434-6fdd-479c-99e0-e9cfa413e2d6/review',
    linkLabel: 'View Course',
    note: 'Password: demo',
    featured: true,
  },
  {
    id: 2,
    category: 'elearning',
    title: 'Goal Setting',
    type: 'Articulate Rise Course',
    description: 'An Articulate Rise course focusing on professional goal-setting frameworks. Content has been redacted for confidentiality; shared here to demonstrate design and instructional approach.',
    tags: ['Articulate Rise', 'Soft Skills', 'Interactive'],
    image: 'https://images.pexels.com/photos/3183153/pexels-photo-3183153.jpeg?auto=compress&cs=tinysrgb&w=800',
    link: 'https://360.articulate.com/review/content/714fad6e-3873-4034-aace-0dc173628eda/review',
    linkLabel: 'View Course',
    note: 'Password: demo · Heavily redacted',
  },
  {
    id: 3,
    category: 'video',
    title: 'Adding the First Knowledge Article',
    type: 'SaaS Product Video',
    description: 'A screen-recorded walkthrough for a beta SaaS knowledge base product, guiding users through adding their first content item. Produced with Camtasia and AI voiceover via ElevenLabs.',
    tags: ['Camtasia', 'ElevenLabs', 'SaaS', 'Product'],
    image: 'https://images.pexels.com/photos/196644/pexels-photo-196644.jpeg?auto=compress&cs=tinysrgb&w=800',
    link: null,
    linkLabel: 'Watch Video',
    note: 'Beta — link available on request',
  },
  {
    id: 4,
    category: 'video',
    title: 'Inviting Users',
    type: 'SaaS Product Video',
    description: 'Step-by-step video tutorial showing administrators how to invite and onboard new users in a SaaS platform. Produced with Camtasia and AI voiceover.',
    tags: ['Camtasia', 'ElevenLabs', 'SaaS', 'Admin'],
    image: 'https://images.pexels.com/photos/3184465/pexels-photo-3184465.jpeg?auto=compress&cs=tinysrgb&w=800',
    link: null,
    linkLabel: 'Watch Video',
    note: 'Beta — link available on request',
  },
  {
    id: 5,
    category: 'video',
    title: 'First Establish Trust',
    type: 'Training Supplemental Video',
    description: 'A standalone training video created to supplement a broader learning program. Uses stock footage combined with AI voiceover to reinforce foundational trust-building concepts.',
    tags: ['Stock Video', 'ElevenLabs', 'Soft Skills'],
    image: 'https://images.pexels.com/photos/3184338/pexels-photo-3184338.jpeg?auto=compress&cs=tinysrgb&w=800',
    link: null,
    linkLabel: 'Watch Video',
    note: 'Available on request',
  },
  {
    id: 6,
    category: 'docs',
    title: 'Adding Your First Knowledge Article',
    type: 'Product Release Notes',
    description: 'Beta release notes written for external SaaS users introducing a new knowledge-base feature. Includes embedded video content and structured guidance for non-technical audiences.',
    tags: ['Release Notes', 'SaaS', 'External Users'],
    image: 'https://images.pexels.com/photos/261763/pexels-photo-261763.jpeg?auto=compress&cs=tinysrgb&w=800',
    link: './Adding_Your_First_Knowledge_Article___Resolve_Customer_Resource_Hub.pdf',
    linkLabel: 'View Document',
    note: null,
  },
  {
    id: 7,
    category: 'docs',
    title: 'Introduction to Dashboard',
    type: 'Product Release Notes',
    description: 'Beta release notes orienting users to a newly launched product dashboard. Clear, task-oriented writing designed for users encountering the product for the first time.',
    tags: ['Release Notes', 'SaaS', 'Onboarding'],
    image: 'https://images.pexels.com/photos/590016/pexels-photo-590016.jpeg?auto=compress&cs=tinysrgb&w=800',
    link: './Introduction_to_RITA_Go_Dashboard___Resolve_Customer_Resource_Hub.pdf',
    linkLabel: 'View Document',
    note: null,
  },
  {
    id: 8,
    category: 'docs',
    title: 'Smart Session Job Aid',
    type: 'Job Aid / Quick Reference',
    description: 'Step-by-step technical job aid for K–12 teachers configuring adaptive learning paths in SmartFox LMS. Covers pre-test setup, module sequencing, quiz thresholds, and troubleshooting — designed for in-the-moment reference during LMS administration.',
    tags: ['Job Aid', 'K–12', 'LMS', 'SmartFox'],
    image: 'https://images.pexels.com/photos/4143791/pexels-photo-4143791.jpeg?auto=compress&cs=tinysrgb&w=800',
    link: './Smart_Session_Job_Aid_v2.pdf',
    linkLabel: 'View PDF',
    note: null,
  },
  {
    id: 9,
    category: 'slides',
    title: 'Articulate Storyline Design Samples',
    type: 'Slide Design · Articulate Storyline',
    description: 'Six slide designs spanning legal compliance, maternal health, healthcare benefits, K–12 curriculum, and environmental safety training — demonstrating visual hierarchy, layout versatility, and client-matched branding across industries.',
    tags: ['Articulate Storyline', 'Visual Design', 'Multi-industry'],
    images: [
      './Jana_Sosnowski_Slide_1.png',
      './Jana_Sosnowski_Slide_2.png',
      './Jana_Sosnowski_Slide_3.png',
      './Jana_Sosnowski_Slide_4.png',
      './Jana_Sosnowski_Slide_5.png',
      './Jana_Sosnowski_Slide_6.png',
    ],
    image: './Jana_Sosnowski_Slide_1.png',
    link: null,
    linkLabel: null,
    note: null,
    featured: true,
    isSlideGallery: true,
  },
]

const filteredItems = computed(() => {
  if (activeCategory.value === 'all') return items
  return items.filter(i => i.category === activeCategory.value)
})
</script>

<style scoped>
.work {
  padding: var(--space-16) var(--space-4);
  background: var(--color-neutral-50);
}

.work__inner {
  max-width: 1200px;
  margin: 0 auto;
}

.work__header {
  text-align: center;
  margin-bottom: var(--space-6);
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
  margin-bottom: var(--space-2);
}

.work__subtitle {
  font-size: 1rem;
  color: var(--color-neutral-500);
  max-width: 520px;
  margin: 0 auto;
  line-height: 1.7;
}

.work__filters {
  display: flex;
  gap: var(--space-1);
  justify-content: center;
  flex-wrap: wrap;
  margin-bottom: var(--space-6);
}

.filter-btn {
  padding: 8px 20px;
  border-radius: 100px;
  border: 1.5px solid var(--color-neutral-200);
  background: white;
  color: var(--color-neutral-600);
  font-size: 0.875rem;
  font-weight: 500;
  cursor: pointer;
  transition: all 0.2s ease;
}

.filter-btn:hover {
  border-color: var(--color-primary);
  color: var(--color-primary);
}

.filter-btn.active {
  background: var(--color-primary);
  border-color: var(--color-primary);
  color: white;
}

.work__grid {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(340px, 1fr));
  gap: var(--space-3);
}

@media (max-width: 600px) {
  .work__grid {
    grid-template-columns: 1fr;
  }
}
</style>
