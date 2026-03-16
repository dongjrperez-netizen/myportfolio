<template>
  <section id="skills" class="skills">
    <div class="container">
      <div class="skills-header">
        <div class="section-tag">Skills</div>
        <h2 class="section-title">My <span>Tech Stack</span></h2>
        <p class="section-sub">Technologies I use to build modern, scalable web applications.</p>
      </div>

      <div class="skills-categories">
        <div v-for="cat in categories" :key="cat.name" class="skill-category">
          <h3 class="cat-title">
            <span class="cat-icon">{{ cat.icon }}</span>
            {{ cat.name }}
          </h3>
          <div class="skill-grid">
            <div
              v-for="skill in cat.skills"
              :key="skill.name"
              class="skill-card"
              :style="`--skill-color: ${skill.color}`"
            >
              <div class="skill-logo" v-html="skill.svg"></div>
              <span class="skill-name">{{ skill.name }}</span>
              <div class="skill-bar">
                <div class="skill-fill" :style="`width: ${skill.level}%`"></div>
              </div>
              <span class="skill-level">{{ skill.level }}%</span>
            </div>
          </div>
        </div>
      </div>

      <div class="tools-row">
        <div class="tools-label">Also familiar with</div>
        <div class="tools-list">
          <span v-for="tool in extraTools" :key="tool" class="tool-tag">{{ tool }}</span>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup>
const categories = [
  {
    name: 'Frontend',
    icon: '🎨',
    skills: [
      { name: 'HTML5', level: 95, color: '#e34f26', svg: `<svg viewBox="0 0 24 24" fill="#e34f26"><path d="M1.5 0h21l-1.91 21.563L11.977 24l-8.565-2.438L1.5 0zm7.031 9.75l-.232-2.718 10.059.003.23-2.622L5.412 4.41l.698 8.01h9.126l-.326 3.426-2.91.804-2.955-.81-.188-2.11H6.248l.33 4.171L12 19.351l5.379-1.443.744-8.157H8.531z"/></svg>` },
      { name: 'CSS3', level: 92, color: '#264de4', svg: `<svg viewBox="0 0 24 24" fill="#264de4"><path d="M1.5 0h21l-1.91 21.563L11.977 24l-8.564-2.438L1.5 0zm17.09 4.413L5.41 4.41l.213 2.622 10.125.002-.255 2.716h-6.64l.24 2.573h6.182l-.366 3.523-2.91.804-2.956-.81-.188-2.11h-2.61l.29 3.855L12 19.288l5.373-1.53L18.59 4.414z"/></svg>` },
      { name: 'JavaScript', level: 90, color: '#f7df1e', svg: `<svg viewBox="0 0 24 24"><rect width="24" height="24" fill="#f7df1e" rx="2"/><path fill="#000" d="M6.001 16.274l1.895-1.145c.365.647.697.195.697-.394v-6.36h2.334v6.394c0 2.168-1.27 3.155-3.124 3.155-1.674 0-2.643-.866-3.132-1.91zM13.3 16.055l1.895-1.1c.5.815 1.149 1.414 2.297 1.414 1.265 0 1.963-.6 1.963-1.53 0-1.046-.766-1.415-2.037-2.03l-.7-.3c-2.017-.865-3.36-1.948-3.36-4.24 0-2.116 1.6-3.727 4.115-3.727 1.782 0 3.065.617 3.98 2.25L20.6 7.898c-.45-.815-1.1-1.265-2.117-1.265-.966 0-1.58.6-1.58 1.265 0 .883.617 1.248 2.016 1.898l.7.298c2.365 1.015 3.715 2.05 3.715 4.39 0 2.515-1.982 3.93-4.63 3.93-2.6 0-4.282-1.232-5.104-2.84l.3-.519z"/></svg>` },
      { name: 'Vue.js', level: 93, color: '#42b883', svg: `<svg viewBox="0 0 24 24" fill="#42b883"><path d="M24 1.61h-9.94L12 5.16 9.94 1.61H0l12 20.78zM12 14.08L5.16 2.23H9.59L12 6.41l2.41-4.18h4.43z"/></svg>` },
    ],
  },
  {
    name: 'Backend',
    icon: '⚙️',
    skills: [
      { name: 'PHP', level: 88, color: '#777bb4', svg: `<svg viewBox="0 0 24 24" fill="#777bb4"><path d="M12 18.08c-6.63 0-12-2.72-12-6.08s5.37-6.08 12-6.08S24 8.64 24 12s-5.37 6.08-12 6.08zm-3.06-8.2c-.51 0-.96.07-1.42.18L6.84 14h1.3l.3-1.48h.79c.98 0 1.45-.5 1.53-1.31.1-.82-.37-1.33-1.82-1.33zm.3 1.02c.53 0 .77.2.7.73-.06.51-.36.73-.88.73h-.62l.25-1.46h.55zm5.6-1.02c-.51 0-.95.07-1.4.18L12.76 14h1.3l.3-1.48h.78c.98 0 1.46-.5 1.53-1.31.1-.82-.37-1.33-1.83-1.33zm.3 1.02c.53 0 .77.2.7.73-.06.51-.36.73-.88.73h-.62l.25-1.46h.55zm3.53-.93h-1.28l-.84 4h1.29l.32-1.68h.54c1.12 0 1.8-.6 1.8-1.62 0-.5-.28-.7-1.83-.7zm.26 1c.34 0 .5.12.5.35 0 .33-.16.5-.49.5h-.43l.17-.85h.25z"/></svg>` },
      { name: 'Laravel', level: 87, color: '#ff2d20', svg: `<svg viewBox="0 0 24 24" fill="#ff2d20"><path d="M23.642 5.43a.364.364 0 0 1 .014.1v5.149c0 .135-.073.26-.189.326l-4.323 2.49v4.934a.378.378 0 0 1-.188.326L9.93 23.949a.316.316 0 0 1-.066.027.236.236 0 0 1-.066.009.236.236 0 0 1-.066-.009.316.316 0 0 1-.066-.027L.512 18.755A.378.378 0 0 1 .323 18.43V3.569a.38.38 0 0 1 .015-.1.389.389 0 0 1 .031-.084.31.31 0 0 1 .014-.023.278.278 0 0 1 .038-.043.316.316 0 0 1 .03-.025.282.282 0 0 1 .05-.025L5.015.041a.378.378 0 0 1 .376 0L9.93 2.577l.038.025c.014.01.027.02.038.031a.282.282 0 0 1 .031.033.248.248 0 0 1 .027.04.239.239 0 0 1 .018.046.228.228 0 0 1 .009.053v4.85l3.947-2.275V.378a.376.376 0 0 1 .188-.326l4.512-2.6a.378.378 0 0 1 .376 0l4.512 2.6a.378.378 0 0 1 .188.326v5.149c0 .128-.068.247-.177.313z"/></svg>` },
      { name: 'Node.js', level: 78, color: '#339933', svg: `<svg viewBox="0 0 24 24" fill="#339933"><path d="M11.998.016a.87.87 0 0 0-.436.117L.439 6.33A.88.88 0 0 0 0 7.091v11.818c0 .31.168.597.439.762l11.123 6.197a.88.88 0 0 0 .877 0l11.123-6.197A.88.88 0 0 0 24 18.91V7.091a.88.88 0 0 0-.439-.761L12.434.133a.87.87 0 0 0-.436-.117z"/></svg>` },
      { name: 'MySQL', level: 85, color: '#4479a1', svg: `<svg viewBox="0 0 24 24" fill="#4479a1"><path d="M16.405 5.501c-.115 0-.193.014-.274.033v.013h.014c.054.104.146.18.214.273.054.107.1.214.154.32l.014-.015c.094-.066.14-.172.14-.333-.04-.047-.046-.094-.08-.14-.04-.067-.1-.1-.18-.151zm-2.956 1.358h-.156c-.09.004-.177.012-.258.021-.134.012-.267.026-.4.046-.227.032-.454.063-.681.092l.012.01c.178.043.353.09.528.135.294.075.587.15.882.225.125.032.25.065.374.1.225.062.447.124.672.185.224.06.45.12.67.18l.04.01c-.39.23-.795.41-1.22.54-.388.12-.79.175-1.194.175-.508 0-.953-.1-1.348-.29-.396-.19-.735-.46-1-.8a3.83 3.83 0 0 1-.596-1.22 4.56 4.56 0 0 1-.193-1.3c0-.44.066-.85.2-1.23.134-.38.334-.705.603-.975.27-.27.6-.478.993-.626.392-.147.842-.22 1.347-.22.474 0 .913.07 1.315.21.4.14.742.35 1.022.624.28.276.497.614.65.997.15.384.227.82.227 1.308z"/></svg>` },
    ],
  },
  {
    name: 'Tools & DevOps',
    icon: '🛠️',
    skills: [
      { name: 'Git', level: 91, color: '#f05032', svg: `<svg viewBox="0 0 24 24" fill="#f05032"><path d="M23.546 10.93L13.067.452a1.55 1.55 0 0 0-2.188 0L8.708 2.627l2.76 2.76a1.838 1.838 0 0 1 2.327 2.341l2.658 2.66a1.838 1.838 0 0 1 1.9 3.039 1.837 1.837 0 0 1-2.6-2.597L13.037 8.3v6.468a1.838 1.838 0 0 1 .48 3.58 1.838 1.838 0 0 1-1.863-3.011l.003-.002V8.23a1.838 1.838 0 0 1-1.004-2.417L7.906 3.063.45 10.517a1.55 1.55 0 0 0 0 2.188l10.48 10.478a1.549 1.549 0 0 0 2.187 0l10.429-10.428a1.55 1.55 0 0 0 0-2.188"/></svg>` },
      { name: 'Docker', level: 72, color: '#2496ed', svg: `<svg viewBox="0 0 24 24" fill="#2496ed"><path d="M13.983 11.078h2.119a.186.186 0 0 0 .186-.185V9.006a.186.186 0 0 0-.186-.186h-2.119a.185.185 0 0 0-.185.185v1.888c0 .102.083.185.185.185m-2.954-5.43h2.118a.186.186 0 0 0 .186-.186V3.574a.186.186 0 0 0-.186-.185h-2.118a.185.185 0 0 0-.185.185v1.888c0 .102.082.185.185.186m0 2.716h2.118a.187.187 0 0 0 .186-.186V6.29a.186.186 0 0 0-.186-.185h-2.118a.185.185 0 0 0-.185.185v1.887c0 .102.082.185.185.186m-2.93 0h2.12a.186.186 0 0 0 .184-.186V6.29a.185.185 0 0 0-.185-.185H8.1a.185.185 0 0 0-.185.185v1.887c0 .102.083.185.185.186m-2.964 0h2.119a.186.186 0 0 0 .185-.186V6.29a.185.185 0 0 0-.185-.185H5.136a.186.186 0 0 0-.186.185v1.887c0 .102.084.185.186.186m5.893 2.715h2.118a.186.186 0 0 0 .186-.185V9.006a.186.186 0 0 0-.186-.186h-2.118a.185.185 0 0 0-.185.185v1.888c0 .102.082.185.185.185m-2.93 0h2.12a.185.185 0 0 0 .184-.185V9.006a.185.185 0 0 0-.184-.186h-2.12a.185.185 0 0 0-.184.185v1.888c0 .102.083.185.185.185m-2.964 0h2.119a.185.185 0 0 0 .185-.185V9.006a.185.185 0 0 0-.184-.186h-2.12a.186.186 0 0 0-.186.186v1.887c0 .102.084.185.186.185m-2.92 0h2.12a.185.185 0 0 0 .184-.185V9.006a.185.185 0 0 0-.184-.186h-2.12a.185.185 0 0 0-.185.186v1.887c0 .102.082.185.185.185M23.763 9.89c-.065-.051-.672-.51-1.954-.51-.338.001-.676.03-1.01.087-.248-1.7-1.653-2.53-1.716-2.566l-.344-.199-.226.327c-.284.438-.49.922-.612 1.43-.23.97-.09 1.882.403 2.661-.595.332-1.55.413-1.744.42H.751a.751.751 0 0 0-.75.748 11.376 11.376 0 0 0 .692 4.062c.545 1.428 1.355 2.48 2.41 3.124 1.18.723 3.1 1.137 5.275 1.137.983.003 1.963-.086 2.93-.266a12.248 12.248 0 0 0 3.823-1.389c.98-.567 1.86-1.288 2.61-2.136 1.252-1.418 1.998-2.997 2.553-4.4h.22c1.372 0 2.215-.549 2.68-1.009.309-.293.55-.65.707-1.046l.098-.288Z"/></svg>` },
      { name: 'VS Code', level: 95, color: '#007acc', svg: `<svg viewBox="0 0 24 24" fill="#007acc"><path d="M23.15 2.587L18.21.21a1.494 1.494 0 0 0-1.705.29l-9.46 8.63-4.12-3.128a.999.999 0 0 0-1.276.057L.327 7.261A1 1 0 0 0 .326 8.74L3.899 12 .326 15.26a1 1 0 0 0 .001 1.479L1.65 17.94a.999.999 0 0 0 1.276.057l4.12-3.128 9.46 8.63a1.492 1.492 0 0 0 1.704.29l4.942-2.377A1.5 1.5 0 0 0 24 19.983V4.017a1.5 1.5 0 0 0-.85-1.43zm-5.146 14.861L10.826 12l7.178-5.448v10.896z"/></svg>` },
      { name: 'Figma', level: 74, color: '#f24e1e', svg: `<svg viewBox="0 0 24 24"><path fill="#0acf83" d="M8 24c2.208 0 4-1.792 4-4v-4H8c-2.208 0-4 1.792-4 4s1.792 4 4 4z"/><path fill="#a259ff" d="M4 12c0-2.208 1.792-4 4-4h4v8H8c-2.208 0-4-1.792-4-4z"/><path fill="#f24e1e" d="M4 4C4 1.792 5.792 0 8 0h4v8H8C5.792 8 4 6.208 4 4z"/><path fill="#ff7262" d="M12 0h4c2.208 0 4 1.792 4 4s-1.792 4-4 4h-4V0z"/><path fill="#1abcfe" d="M20 12c0 2.208-1.792 4-4 4s-4-1.792-4-4 1.792-4 4-4 4 1.792 4 4z"/></svg>` },
    ],
  },
]

const extraTools = ['Tailwind CSS', 'REST API', 'Bootstrap','TypeScript']
</script>

<style scoped>
.skills {
  padding: 120px 0;
}

.skills-header {
  text-align: center;
  margin-bottom: 64px;
}

.skills-header .section-tag {
  margin: 0 auto 20px;
}

.skills-header .section-sub {
  margin: 0 auto;
  text-align: center;
}

.skills-categories {
  display: flex;
  flex-direction: column;
  gap: 48px;
}

.skill-category {
  background: var(--bg-card);
  border: 1px solid var(--border);
  border-radius: var(--radius-lg);
  padding: 32px;
}

.cat-title {
  font-family: var(--font-display);
  font-size: 1rem;
  font-weight: 700;
  color: var(--text-muted);
  text-transform: uppercase;
  letter-spacing: 0.1em;
  margin-bottom: 24px;
  display: flex;
  align-items: center;
  gap: 10px;
}

.cat-icon { font-size: 1.2rem; }

.skill-grid {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(220px, 1fr));
  gap: 16px;
}

.skill-card {
  background: var(--bg);
  border: 1px solid var(--border);
  border-radius: var(--radius);
  padding: 20px;
  transition: var(--transition);
  display: flex;
  flex-direction: column;
  gap: 10px;
}

.skill-card:hover {
  border-color: var(--skill-color, var(--accent));
  transform: translateY(-3px);
  box-shadow: 0 12px 32px rgba(0,0,0,0.2);
}

.skill-logo {
  width: 36px;
  height: 36px;
}

.skill-logo :deep(svg) {
  width: 100%;
  height: 100%;
}

.skill-name {
  font-family: var(--font-display);
  font-size: 14px;
  font-weight: 600;
  color: var(--text);
}

.skill-bar {
  height: 4px;
  background: var(--border);
  border-radius: 2px;
  overflow: hidden;
}

.skill-fill {
  height: 100%;
  background: var(--skill-color, var(--accent));
  border-radius: 2px;
  transition: width 1.2s cubic-bezier(0.4, 0, 0.2, 1);
}

.skill-level {
  font-size: 11px;
  color: var(--text-muted);
  font-weight: 500;
}

/* Extra tools */
.tools-row {
  margin-top: 48px;
  display: flex;
  align-items: center;
  gap: 20px;
  flex-wrap: wrap;
}

.tools-label {
  font-size: 13px;
  color: var(--text-muted);
  font-weight: 500;
  white-space: nowrap;
  flex-shrink: 0;
}

.tools-list {
  display: flex;
  flex-wrap: wrap;
  gap: 8px;
}

.tool-tag {
  font-size: 12px;
  font-weight: 500;
  color: var(--text-muted);
  background: var(--bg-card);
  border: 1px solid var(--border);
  padding: 4px 12px;
  border-radius: 100px;
  transition: var(--transition);
}

.tool-tag:hover {
  color: var(--accent);
  border-color: var(--border-accent);
}

@media (max-width: 640px) {
  .skill-category { padding: 20px; }
  .skill-grid { grid-template-columns: 1fr 1fr; }
}
</style>
