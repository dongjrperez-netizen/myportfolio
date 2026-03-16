<template>
  <section id="about" class="about">
    <div class="container about-inner">
      <div class="about-image-col" ref="imgRef">
        <div class="about-img-frame">
          <img
            src="/image.jpg"
            alt="Alex Rivera"
            class="about-img"
          />
          <div class="about-img-accent"></div>
        </div>
      </div>

      <div class="about-content" ref="contentRef">
        <div class="section-tag">About Me</div>
        <h2 class="section-title">Turning ideas into<br /><span>digital reality</span></h2>

        <p class="about-bio">
          I'm a Full Stack Developer based in Davao City, Philippines, with 5+ years of
          experience building web applications that are fast, accessible, and delightful to use.
          I thrive at the intersection of design and engineering — I care deeply about how things
          look and how they work.
        </p>

        <p class="about-bio">
          My journey started with a passion for problem-solving and grew into a career crafting
          everything from dynamic SPAs with Vue.js to robust REST APIs with Laravel. I enjoy
          working closely with clients and teams to ship products that actually matter.
        </p>

        <div class="about-details">
          <div v-for="item in details" :key="item.label" class="detail-item">
            <span class="detail-icon">{{ item.icon }}</span>
            <div>
              <div class="detail-label">{{ item.label }}</div>
              <div class="detail-value">{{ item.value }}</div>
            </div>
          </div>
        </div>

        <!-- <div class="about-edu">
          <h3 class="edu-heading">Education & Experience</h3>
          <div class="timeline">
            <div v-for="entry in timeline" :key="entry.year" class="timeline-item">
              <div class="timeline-dot"></div>
              <div class="timeline-content">
                <span class="timeline-year">{{ entry.year }}</span>
                <div class="timeline-title">{{ entry.title }}</div>
                <div class="timeline-place">{{ entry.place }}</div>
              </div>
            </div>
          </div>
        </div> -->
      </div>
    </div>
  </section>
</template>

<script setup>
const details = [
  { icon: '📍', label: 'Location', value: 'Davao City, Philippines' },
  { icon: '📧', label: 'Email', value: 'alex@example.com' },
  { icon: '🎯', label: 'Availability', value: 'Open to opportunities' },
  { icon: '💼', label: 'Graduating', value: '2026' },
]

const timeline = [
  { year: '2023–Present', title: 'Senior Full Stack Developer', place: 'TechCorp Solutions' },
  { year: '2021–2023', title: 'Full Stack Developer', place: 'Freelance / Remote' },
  { year: '2019–2021', title: 'Junior Web Developer', place: 'WebCraft Studio' },
  { year: '2015–2019', title: 'BS Computer Science', place: 'Ateneo de Davao University' },
]
</script>

<style scoped>
.about {
  padding: 120px 0;
  background: linear-gradient(180deg, var(--bg) 0%, var(--bg-2) 50%, var(--bg) 100%);
}

.about-inner {
  display: grid;
  grid-template-columns: 1fr 1.2fr;
  gap: 80px;
  align-items: center;
}

/* Image col */
.about-image-col {
  position: relative;
}

.about-img-frame {
  position: relative;
  border-radius: var(--radius-lg);
  overflow: hidden;
  aspect-ratio: 3/4;
  max-width: 380px;
}

.about-img {
  width: 100%;
  height: 100%;
  object-fit: cover;
  background: var(--bg-card);
}

.about-img-accent {
  position: absolute;
  inset: 0;
  background: linear-gradient(135deg, transparent 60%, rgba(99,209,175,0.15));
  border: 2px solid var(--border-accent);
  border-radius: var(--radius-lg);
  pointer-events: none;
}

.experience-badge {
  position: absolute;
  bottom: -20px;
  right: -20px;
  background: var(--accent);
  color: var(--bg);
  border-radius: var(--radius-lg);
  padding: 20px 24px;
  text-align: center;
  box-shadow: 0 16px 48px rgba(99, 209, 175, 0.3);
}

.exp-number {
  font-family: var(--font-display);
  font-size: 2.5rem;
  font-weight: 800;
  line-height: 1;
}

.exp-label {
  font-size: 12px;
  font-weight: 500;
  line-height: 1.4;
  margin-top: 4px;
}

/* Content */
.about-bio {
  color: var(--text-muted);
  line-height: 1.8;
  margin-bottom: 16px;
}

.about-details {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 16px;
  margin: 32px 0;
  padding: 24px;
  background: var(--bg-card);
  border: 1px solid var(--border);
  border-radius: var(--radius);
}

.detail-item {
  display: flex;
  align-items: flex-start;
  gap: 12px;
}

.detail-icon { font-size: 1.2rem; margin-top: 2px; }

.detail-label {
  font-size: 11px;
  color: var(--text-muted);
  letter-spacing: 0.08em;
  text-transform: uppercase;
  margin-bottom: 2px;
}

.detail-value {
  font-size: 14px;
  font-weight: 500;
  color: var(--text);
}

/* Timeline */
.edu-heading {
  font-family: var(--font-display);
  font-size: 1rem;
  font-weight: 700;
  color: var(--text);
  margin-bottom: 20px;
  letter-spacing: 0.05em;
}

.timeline {
  position: relative;
  padding-left: 24px;
  border-left: 2px solid var(--border);
}

.timeline-item {
  position: relative;
  padding-bottom: 24px;
}

.timeline-item:last-child { padding-bottom: 0; }

.timeline-dot {
  position: absolute;
  left: -31px;
  top: 5px;
  width: 10px;
  height: 10px;
  border-radius: 50%;
  background: var(--accent);
  border: 2px solid var(--bg);
  box-shadow: 0 0 0 3px rgba(99,209,175,0.2);
}

.timeline-year {
  font-size: 11px;
  color: var(--accent);
  font-weight: 600;
  letter-spacing: 0.05em;
  font-family: var(--font-display);
}

.timeline-title {
  font-weight: 600;
  color: var(--text);
  margin: 4px 0 2px;
  font-size: 15px;
}

.timeline-place {
  font-size: 13px;
  color: var(--text-muted);
}

@media (max-width: 900px) {
  .about-inner {
    grid-template-columns: 1fr;
    gap: 48px;
  }
  .about-img-frame {
    max-width: 280px;
    margin: 0 auto;
    aspect-ratio: 1;
    border-radius: 50%;
  }
  .about-img-accent { border-radius: 50%; }
  .experience-badge { right: 0; }
}

@media (max-width: 480px) {
  .about-details { grid-template-columns: 1fr; }
}
</style>
