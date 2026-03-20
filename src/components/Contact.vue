<template>
  <section id="contact" class="contact">
    <div class="contact-glow"></div>
    <div class="container contact-inner">
      <div class="contact-info">
        <div class="section-tag">Contact</div>
        <h2 class="section-title">Let's build<br /><span>something great</span></h2>
        <p class="section-sub">
          Whether you have a project in mind, a question, or just want to say hello — my inbox is always open.
        </p>

        <div class="contact-cards">
          <a
            v-for="card in contactCards"
            :key="card.label"
            :href="card.href"
            target="_blank"
            class="contact-card"
          >
            <div class="contact-card-icon" v-html="card.icon"></div>
            <div>
              <div class="contact-card-label">{{ card.label }}</div>
              <div class="contact-card-value">{{ card.value }}</div>
            </div>
            <svg class="contact-card-arrow" width="16" height="16" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2">
              <path d="M5 12h14M12 5l7 7-7 7"/>
            </svg>
          </a>
        </div>

        <div class="social-links">
          <a v-for="s in socials" :key="s.name" :href="s.href" target="_blank" class="social-link" :title="s.name">
            <span v-html="s.icon"></span>
          </a>
        </div>
      </div>

      <div class="contact-form-wrap">
        <div class="form-card">
          <h3 class="form-title">Send a Message</h3>
          <p class="form-sub">I'll get back to you within 24 hours.</p>

          <form @submit.prevent="handleSubmit" class="form" novalidate>
            <div class="form-row">
              <div class="form-group" :class="{ error: errors.name }">
                <label for="name">Your Name</label>
                <input
                  id="name"
                  v-model="form.name"
                  type="text"
                  placeholder="John Doe"
                  autocomplete="name"
                />
                <span class="error-msg" v-if="errors.name">{{ errors.name }}</span>
              </div>
              <div class="form-group" :class="{ error: errors.email }">
                <label for="email">Email Address</label>
                <input
                  id="email"
                  v-model="form.email"
                  type="email"
                  placeholder="john@example.com"
                  autocomplete="email"
                />
                <span class="error-msg" v-if="errors.email">{{ errors.email }}</span>
              </div>
            </div>

            <div class="form-group" :class="{ error: errors.subject }">
              <label for="subject">Subject</label>
              <input
                id="subject"
                v-model="form.subject"
                type="text"
                placeholder="Project inquiry..."
              />
              <span class="error-msg" v-if="errors.subject">{{ errors.subject }}</span>
            </div>

            <div class="form-group" :class="{ error: errors.message }">
              <label for="message">Message</label>
              <textarea
                id="message"
                v-model="form.message"
                rows="5"
                placeholder="Tell me about your project, timeline, and budget..."
              ></textarea>
              <span class="error-msg" v-if="errors.message">{{ errors.message }}</span>
              <span class="char-count">{{ form.message.length }} / 1000</span>
            </div>

            <button type="submit" class="btn btn-primary submit-btn" :disabled="submitting">
              <span v-if="submitting">Sending...</span>
              <span v-else-if="submitted">Message Sent! ✓</span>
              <span v-else>
                Send Message
                <svg width="16" height="16" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2">
                  <line x1="22" y1="2" x2="11" y2="13"/><polygon points="22 2 15 22 11 13 2 9 22 2"/>
                </svg>
              </span>
            </button>
          </form>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup>
import { ref, reactive } from 'vue'

const form = reactive({ name: '', email: '', subject: '', message: '' })
const errors = reactive({ name: '', email: '', subject: '', message: '' })
const submitting = ref(false)
const submitted = ref(false)

const contactCards = [
  {
    label: 'Email',
    value: 'rogerjrperez286@gmail.com',
    href: 'mailto:rogerjrperez286@gmail.com',
    icon: `<svg width="20" height="20" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.8"><rect x="2" y="4" width="20" height="16" rx="2"/><path d="M2 7l10 7 10-7"/></svg>`,
  },
  {
    label: 'LinkedIn',
    value: 'linkedin.com/in/rogerperez',
    href: 'https://linkedin.com',
    icon: `<svg width="20" height="20" viewBox="0 0 24 24" fill="currentColor"><path d="M16 8a6 6 0 016 6v7h-4v-7a2 2 0 00-2-2 2 2 0 00-2 2v7h-4v-7a6 6 0 016-6zM2 9h4v12H2z"/><circle cx="4" cy="4" r="2"/></svg>`,
  },
  {
    label: 'GitHub',
    value: 'github.com/rogerperez',
    href: 'https://github.com',
    icon: `<svg width="20" height="20" viewBox="0 0 24 24" fill="currentColor"><path d="M12 0C5.374 0 0 5.373 0 12c0 5.302 3.438 9.8 8.207 11.387.599.111.793-.261.793-.577v-2.234c-3.338.726-4.033-1.416-4.033-1.416-.546-1.387-1.333-1.756-1.333-1.756-1.089-.745.083-.729.083-.729 1.205.084 1.839 1.237 1.839 1.237 1.07 1.834 2.807 1.304 3.492.997.107-.775.418-1.305.762-1.604-2.665-.305-5.467-1.334-5.467-5.931 0-1.311.469-2.381 1.236-3.221-.124-.303-.535-1.524.117-3.176 0 0 1.008-.322 3.301 1.23A11.509 11.509 0 0112 5.803c1.02.005 2.047.138 3.006.404 2.291-1.552 3.297-1.23 3.297-1.23.653 1.653.242 2.874.118 3.176.77.84 1.235 1.911 1.235 3.221 0 4.609-2.807 5.624-5.479 5.921.43.372.823 1.102.823 2.222v3.293c0 .319.192.694.801.576C20.566 21.797 24 17.3 24 12c0-6.627-5.373-12-12-12z"/></svg>`,
  },
]

const socials = [
  { name: 'GitHub', href: 'https://github.com', icon: `<svg width="20" height="20" viewBox="0 0 24 24" fill="currentColor"><path d="M12 0C5.374 0 0 5.373 0 12c0 5.302 3.438 9.8 8.207 11.387.599.111.793-.261.793-.577v-2.234c-3.338.726-4.033-1.416-4.033-1.416-.546-1.387-1.333-1.756-1.333-1.756-1.089-.745.083-.729.083-.729 1.205.084 1.839 1.237 1.839 1.237 1.07 1.834 2.807 1.304 3.492.997.107-.775.418-1.305.762-1.604-2.665-.305-5.467-1.334-5.467-5.931 0-1.311.469-2.381 1.236-3.221-.124-.303-.535-1.524.117-3.176 0 0 1.008-.322 3.301 1.23A11.509 11.509 0 0112 5.803c1.02.005 2.047.138 3.006.404 2.291-1.552 3.297-1.23 3.297-1.23.653 1.653.242 2.874.118 3.176.77.84 1.235 1.911 1.235 3.221 0 4.609-2.807 5.624-5.479 5.921.43.372.823 1.102.823 2.222v3.293c0 .319.192.694.801.576C20.566 21.797 24 17.3 24 12c0-6.627-5.373-12-12-12z"/></svg>` },
  { name: 'LinkedIn', href: 'https://linkedin.com', icon: `<svg width="20" height="20" viewBox="0 0 24 24" fill="currentColor"><path d="M16 8a6 6 0 016 6v7h-4v-7a2 2 0 00-2-2 2 2 0 00-2 2v7h-4v-7a6 6 0 016-6zM2 9h4v12H2z"/><circle cx="4" cy="4" r="2"/></svg>` },
  { name: 'Twitter', href: 'https://twitter.com', icon: `<svg width="20" height="20" viewBox="0 0 24 24" fill="currentColor"><path d="M18.244 2.25h3.308l-7.227 8.26 8.502 11.24H16.17l-5.214-6.817L4.99 21.75H1.68l7.73-8.835L1.254 2.25H8.08l4.713 6.231zm-1.161 17.52h1.833L7.084 4.126H5.117z"/></svg>` },
  { name: 'Email', href: 'mailto:alex@example.com', icon: `<svg width="20" height="20" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.8"><rect x="2" y="4" width="20" height="16" rx="2"/><path d="M2 7l10 7 10-7"/></svg>` },
]

function validate() {
  let valid = true
  Object.keys(errors).forEach(k => errors[k] = '')
  if (!form.name.trim()) { errors.name = 'Name is required.'; valid = false }
  if (!form.email.trim()) { errors.email = 'Email is required.'; valid = false }
  else if (!/^[^\s@]+@[^\s@]+\.[^\s@]+$/.test(form.email)) { errors.email = 'Enter a valid email.'; valid = false }
  if (!form.subject.trim()) { errors.subject = 'Subject is required.'; valid = false }
  if (!form.message.trim()) { errors.message = 'Message is required.'; valid = false }
  else if (form.message.length < 10) { errors.message = 'Message is too short.'; valid = false }
  return valid
}

async function handleSubmit() {
  if (!validate()) return
  submitting.value = true
  await new Promise(r => setTimeout(r, 1500))
  submitting.value = false
  submitted.value = true
  Object.keys(form).forEach(k => form[k] = '')
  setTimeout(() => submitted.value = false, 4000)
}
</script>

<style scoped>
.contact {
  padding: 120px 0;
  position: relative;
  overflow: hidden;
  background: var(--bg-2);
}

.contact-glow {
  position: absolute;
  width: 600px; height: 600px;
  background: radial-gradient(circle, rgba(99,209,175,0.06), transparent 70%);
  bottom: -200px; left: -100px;
  pointer-events: none;
}

.contact-inner {
  display: grid;
  grid-template-columns: 1fr 1.2fr;
  gap: 80px;
  align-items: start;
  position: relative;
  z-index: 1;
}

/* Info col */
.contact-cards {
  display: flex;
  flex-direction: column;
  gap: 12px;
  margin: 36px 0;
}

.contact-card {
  display: flex;
  align-items: center;
  gap: 16px;
  padding: 16px 20px;
  background: var(--bg-card);
  border: 1px solid var(--border);
  border-radius: var(--radius);
  transition: var(--transition);
}

.contact-card:hover {
  border-color: var(--border-accent);
  transform: translateX(4px);
}

.contact-card-icon {
  width: 40px; height: 40px;
  display: flex;
  align-items: center;
  justify-content: center;
  background: var(--accent-glow);
  border-radius: 10px;
  color: var(--accent);
  flex-shrink: 0;
}

.contact-card-label {
  font-size: 11px;
  color: var(--text-muted);
  letter-spacing: 0.08em;
  text-transform: uppercase;
  margin-bottom: 2px;
}

.contact-card-value {
  font-size: 14px;
  font-weight: 500;
  color: var(--text);
}

.contact-card-arrow {
  margin-left: auto;
  color: var(--text-faint);
  flex-shrink: 0;
  transition: var(--transition);
}

.contact-card:hover .contact-card-arrow {
  color: var(--accent);
  transform: translateX(3px);
}

.social-links {
  display: flex;
  gap: 12px;
}

.social-link {
  width: 42px; height: 42px;
  display: flex;
  align-items: center;
  justify-content: center;
  background: var(--bg-card);
  border: 1px solid var(--border);
  border-radius: var(--radius);
  color: var(--text-muted);
  transition: var(--transition);
}

.social-link:hover {
  color: var(--accent);
  border-color: var(--border-accent);
  transform: translateY(-3px);
}

/* Form */
.form-card {
  background: var(--bg-card);
  border: 1px solid var(--border);
  border-radius: var(--radius-lg);
  padding: 40px;
}

.form-title {
  font-family: var(--font-display);
  font-size: 1.3rem;
  font-weight: 700;
  color: var(--text);
  margin-bottom: 6px;
}

.form-sub {
  font-size: 14px;
  color: var(--text-muted);
  margin-bottom: 32px;
}

.form { display: flex; flex-direction: column; gap: 20px; }

.form-row {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 16px;
}

.form-group {
  display: flex;
  flex-direction: column;
  gap: 6px;
  position: relative;
}

label {
  font-size: 13px;
  font-weight: 500;
  color: var(--text-muted);
  letter-spacing: 0.03em;
}

input, textarea {
  background: var(--bg);
  border: 1px solid var(--border);
  border-radius: var(--radius);
  color: var(--text);
  font-family: var(--font-body);
  font-size: 14px;
  padding: 12px 16px;
  transition: var(--transition);
  resize: vertical;
  outline: none;
  width: 100%;
}

input::placeholder, textarea::placeholder {
  color: var(--text-faint);
}

input:focus, textarea:focus {
  border-color: var(--accent);
  box-shadow: 0 0 0 3px var(--accent-glow);
}

.form-group.error input,
.form-group.error textarea {
  border-color: #ef4444;
}

.error-msg {
  font-size: 12px;
  color: #ef4444;
}

.char-count {
  position: absolute;
  right: 0;
  bottom: -20px;
  font-size: 11px;
  color: var(--text-faint);
}

.submit-btn {
  width: 100%;
  justify-content: center;
  padding: 14px;
  font-size: 15px;
  margin-top: 8px;
}

.submit-btn:disabled {
  opacity: 0.7;
  cursor: not-allowed;
  transform: none !important;
}

@media (max-width: 900px) {
  .contact-inner {
    grid-template-columns: 1fr;
    gap: 48px;
  }
}

@media (max-width: 480px) {
  .form-row { grid-template-columns: 1fr; }
  .form-card { padding: 24px; }
}
</style>
