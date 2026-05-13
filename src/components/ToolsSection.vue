<template>
  <section id="tools" class="tools">
    <div class="tools__inner">
      <div class="tools__header">
        <p class="section-eyebrow">Skills & Tools</p>
        <h2 class="section-title">What I Work With</h2>
      </div>
      <div class="tools__grid">
        <div v-for="group in toolGroups" :key="group.category" class="tool-group">
          <h3 class="tool-group__title">{{ group.category }}</h3>
          <ul class="tool-group__list">
            <li v-for="tool in group.tools" :key="tool" class="tool-item">
              <span class="tool-item__dot"></span>
              {{ tool }}
            </li>
          </ul>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup>
const toolGroups = [
  {
    category: 'E-Learning Authoring',
    tools: ['Articulate Storyline', 'Articulate Rise', 'iSpring', 'SCORM / xAPI', 'LMS Publishing'],
  },
  {
    category: 'Video & Multimedia',
    tools: ['Camtasia', 'Descript', 'ElevenLabs (AI Voiceover)', 'Pictory.ai', 'Canva'],
  },
  {
    category: 'Technical Writing & Docs',
    tools: ['Docs-as-Code (Docusaurus)', 'Markdown', 'Release Notes', 'User Guides', 'Job Aids'],
  },
  {
    category: 'LMS Platforms',
    tools: ['Docebo', 'LearnWorlds', 'TalentLMS', 'SAP Litmos', 'Canvas', 'Moodle'],
  },
  {
    category: 'Dev & Workflow Tools',
    tools: ['Git / GitHub', 'Python (Automation)', 'JIRA', 'Confluence', 'Trello'],
  },
  {
    category: 'Approach & Domains',
    tools: ['ADDIE / SAM', 'SME Facilitation', 'Curriculum Architecture', 'SaaS / Cloud', 'Healthcare & K–12'],
  },
]
</script>

<style scoped>
.tools {
  padding: var(--space-16) var(--space-4);
  background: linear-gradient(160deg, #0f3d52 0%, #1e5f74 100%);
}

.tools__inner {
  max-width: 1200px;
  margin: 0 auto;
}

.tools__header {
  text-align: center;
  margin-bottom: var(--space-8);
}

.section-eyebrow {
  font-size: 0.78rem;
  font-weight: 600;
  letter-spacing: 0.14em;
  text-transform: uppercase;
  color: var(--color-accent-light);
  margin-bottom: var(--space-2);
}

.section-title {
  font-family: var(--font-display);
  font-size: clamp(1.8rem, 4vw, 2.8rem);
  color: white;
}

.tools__grid {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: var(--space-4);
}

.tool-group {
  background: rgba(255, 255, 255, 0.07);
  border: 1px solid rgba(255, 255, 255, 0.12);
  border-radius: 14px;
  padding: var(--space-4);
  transition: background 0.2s ease;
}

.tool-group:hover {
  background: rgba(255, 255, 255, 0.11);
}

.tool-group__title {
  font-size: 0.78rem;
  font-weight: 700;
  letter-spacing: 0.1em;
  text-transform: uppercase;
  color: var(--color-accent-light);
  margin-bottom: var(--space-3);
}

.tool-group__list {
  list-style: none;
  display: flex;
  flex-direction: column;
  gap: 10px;
}

.tool-item {
  display: flex;
  align-items: center;
  gap: 10px;
  font-size: 0.9rem;
  color: rgba(255, 255, 255, 0.8);
}

.tool-item__dot {
  width: 6px;
  height: 6px;
  border-radius: 50%;
  background: var(--color-accent-light);
  flex-shrink: 0;
}

@media (max-width: 900px) {
  .tools__grid {
    grid-template-columns: repeat(2, 1fr);
  }
}

@media (max-width: 600px) {
  .tools__grid {
    grid-template-columns: 1fr;
  }
}
</style>
