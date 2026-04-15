<template>
  <section id="contact" class="contact">

    <!-- Background -->
    <div class="contact__bg" aria-hidden="true">
      <div class="contact__bg-glow"></div>
      <div class="contact__bg-grid"></div>
      <div class="contact__bg-lines"></div>
    </div>

    <div class="contact__container">

      <!-- ── LEFT — Info column ── -->
      <div class="contact__left">

        <div class="contact__eyebrow">
          <span class="contact__eyebrow-line"></span>
          <span>Get In Touch</span>
        </div>

        <h2 class="contact__heading">
          <span class="contact__heading-line">Let's Build</span>
          <span class="contact__heading-line contact__heading-line--ghost">Your Financial</span>
          <span class="contact__heading-line contact__heading-line--coral">Future.</span>
        </h2>

        <p class="contact__sub">
          Whether you're beginning your investment journey or managing
          institutional capital, our advisors are ready to craft a
          strategy built around your goals.
        </p>

        <!-- Contact details -->
        <ul class="contact__details">
          <li v-for="detail in details" :key="detail.label" class="contact__detail">
            <span class="contact__detail-icon" v-html="detail.icon"></span>
            <div>
              <span class="contact__detail-label">{{ detail.label }}</span>
              <a :href="detail.href" class="contact__detail-value">{{ detail.value }}</a>
            </div>
          </li>
        </ul>

        <!-- Office locations -->
        <div class="contact__offices">
          <span class="contact__offices-label">Our Offices</span>
          <div class="contact__offices-list">
            <div v-for="office in offices" :key="office.city" class="contact__office">
              <span class="contact__office-dot"></span>
              <div>
                <div class="contact__office-city">{{ office.city }}</div>
                <div class="contact__office-addr">{{ office.address }}</div>
              </div>
            </div>
          </div>
        </div>

      </div>

      <!-- ── RIGHT — Form ── -->
      <div class="contact__right">
        <div class="contact__form-card">

          <!-- Card header -->
          <div class="contact__form-header">
            <span class="contact__form-title">Schedule a Consultation</span>
            <span class="contact__form-sub">Free · No obligation · 30 minutes</span>
          </div>

          <!-- Form -->
          <form class="contact__form" @submit.prevent="handleSubmit" novalidate>

            <!-- Row 1 -->
            <div class="contact__form-row">
              <div class="contact__field" :class="{ 'contact__field--error': errors.firstName }">
                <label class="contact__label">First Name</label>
                <div class="contact__input-wrap">
                  <input
                    v-model="form.firstName"
                    type="text"
                    class="contact__input"
                    placeholder="James"
                    @focus="focused = 'firstName'"
                    @blur="focused = null; validateField('firstName')"
                  />
                  <span class="contact__input-line"></span>
                </div>
                <span v-if="errors.firstName" class="contact__error">{{ errors.firstName }}</span>
              </div>

              <div class="contact__field" :class="{ 'contact__field--error': errors.lastName }">
                <label class="contact__label">Last Name</label>
                <div class="contact__input-wrap">
                  <input
                    v-model="form.lastName"
                    type="text"
                    class="contact__input"
                    placeholder="Harderlin"
                    @focus="focused = 'lastName'"
                    @blur="focused = null; validateField('lastName')"
                  />
                  <span class="contact__input-line"></span>
                </div>
                <span v-if="errors.lastName" class="contact__error">{{ errors.lastName }}</span>
              </div>
            </div>

            <!-- Email -->
            <div class="contact__field" :class="{ 'contact__field--error': errors.email }">
              <label class="contact__label">Email Address</label>
              <div class="contact__input-wrap">
                <input
                  v-model="form.email"
                  type="email"
                  class="contact__input"
                  placeholder="james@example.com"
                  @focus="focused = 'email'"
                  @blur="focused = null; validateField('email')"
                />
                <span class="contact__input-line"></span>
              </div>
              <span v-if="errors.email" class="contact__error">{{ errors.email }}</span>
            </div>

            <!-- Investment Range -->
            <div class="contact__field">
              <label class="contact__label">Investment Range</label>
              <div class="contact__input-wrap contact__input-wrap--select">
                <select v-model="form.range" class="contact__input contact__select">
                  <option value="" disabled>Select your range</option>
                  <option v-for="r in ranges" :key="r" :value="r">{{ r }}</option>
                </select>
                <span class="contact__select-arrow">
                  <svg width="12" height="12" viewBox="0 0 12 12" fill="none">
                    <path d="M2 4l4 4 4-4" stroke="currentColor" stroke-width="1.4" stroke-linecap="round" stroke-linejoin="round"/>
                  </svg>
                </span>
                <span class="contact__input-line"></span>
              </div>
            </div>

            <!-- Interest -->
            <div class="contact__field">
              <label class="contact__label">Area of Interest</label>
              <div class="contact__interests">
                <button
                  v-for="interest in interests"
                  :key="interest"
                  type="button"
                  :class="['contact__interest-btn', { 'contact__interest-btn--active': form.interests.includes(interest) }]"
                  @click="toggleInterest(interest)"
                >
                  {{ interest }}
                </button>
              </div>
            </div>

            <!-- Message -->
            <div class="contact__field">
              <label class="contact__label">Message <span class="contact__label-opt">(Optional)</span></label>
              <div class="contact__input-wrap">
                <textarea
                  v-model="form.message"
                  class="contact__input contact__textarea"
                  placeholder="Tell us about your investment goals..."
                  rows="3"
                  @focus="focused = 'message'"
                  @blur="focused = null"
                ></textarea>
                <span class="contact__input-line"></span>
              </div>
            </div>

            <!-- Submit -->
            <button type="submit" class="contact__submit" :class="{ 'contact__submit--loading': loading, 'contact__submit--done': submitted }">
              <span v-if="!submitted" class="contact__submit-inner">
                <span v-if="!loading">
                  Book Your Consultation
                  <svg width="16" height="16" viewBox="0 0 16 16" fill="none">
                    <path d="M3 8h10M9 4l4 4-4 4" stroke="currentColor" stroke-width="1.4" stroke-linecap="round" stroke-linejoin="round"/>
                  </svg>
                </span>
                <span v-else class="contact__spinner"></span>
              </span>
              <span v-else class="contact__submit-success">
                ✓ &nbsp;We'll be in touch soon
              </span>
            </button>

            <p class="contact__form-note">
              By submitting you agree to our privacy policy. We never share your data.
            </p>

          </form>
        </div>
      </div>

    </div>
  </section>
</template>

<script>
export default {
  name: 'ContactSection',
  data() {
    return {
      focused: null,
      loading: false,
      submitted: false,
      form: {
        firstName: '',
        lastName: '',
        email: '',
        range: '',
        interests: [],
        message: '',
      },
      errors: {
        firstName: '',
        lastName: '',
        email: '',
      },
      ranges: [
        'Under $50,000',
        '$50,000 – $250,000',
        '$250,000 – $1M',
        '$1M – $5M',
        '$5M – $20M',
        '$20M+',
      ],
      interests: [
        'Wealth Management',
        'Private Equity',
        'Fixed Income',
        'Retirement',
        'Global Markets',
        'Alternatives',
      ],
      details: [
        {
          label: 'Email Us',
          value: 'advisory@harderlin.com',
          href: 'mailto:advisory@harderlin.com',
          icon: `<svg width="20" height="20" viewBox="0 0 20 20" fill="none">
                   <rect x="2" y="4" width="16" height="12" rx="2" stroke="#FF6B5B" stroke-width="1.4"/>
                   <path d="M2 7l8 5 8-5" stroke="#FF6B5B" stroke-width="1.4" stroke-linecap="round"/>
                 </svg>`,
        },
        {
          label: 'Call Us',
          value: '+1 (212) 555-0192',
          href: 'tel:+12125550192',
          icon: `<svg width="20" height="20" viewBox="0 0 20 20" fill="none">
                   <path d="M4 3h3.5l1.5 4-2 1.5c1 2 2.5 3.5 4.5 4.5L13 11l4 1.5V16a1 1 0 01-1 1C6 17 3 8 3 4a1 1 0 011-1z" stroke="#FF6B5B" stroke-width="1.4" stroke-linejoin="round"/>
                 </svg>`,
        },
        {
          label: 'Headquarters',
          value: '1 World Trade Center, New York',
          href: '#',
          icon: `<svg width="20" height="20" viewBox="0 0 20 20" fill="none">
                   <path d="M10 2C7.2 2 5 4.2 5 7c0 4 5 11 5 11s5-7 5-11c0-2.8-2.2-5-5-5z" stroke="#FF6B5B" stroke-width="1.4"/>
                   <circle cx="10" cy="7" r="2" stroke="#FF6B5B" stroke-width="1.4"/>
                 </svg>`,
        },
      ],
      offices: [
        { city: 'New York',  address: '1 World Trade Center, Suite 8500' },
        { city: 'London',    address: '30 St Mary Axe, EC3A 8BF' },
        { city: 'Singapore', address: '1 Raffles Place, Tower 1' },
      ],
    };
  },
  methods: {
    toggleInterest(interest) {
      const idx = this.form.interests.indexOf(interest);
      if (idx === -1) this.form.interests.push(interest);
      else this.form.interests.splice(idx, 1);
    },
    validateField(field) {
      if (field === 'firstName') {
        this.errors.firstName = this.form.firstName.trim() ? '' : 'First name is required';
      }
      if (field === 'lastName') {
        this.errors.lastName = this.form.lastName.trim() ? '' : 'Last name is required';
      }
      if (field === 'email') {
        const valid = /^[^\s@]+@[^\s@]+\.[^\s@]+$/.test(this.form.email);
        this.errors.email = this.form.email ? (valid ? '' : 'Please enter a valid email') : 'Email is required';
      }
    },
    validateAll() {
      this.validateField('firstName');
      this.validateField('lastName');
      this.validateField('email');
      return !this.errors.firstName && !this.errors.lastName && !this.errors.email;
    },
    handleSubmit() {
      if (!this.validateAll()) return;
      this.loading = true;
      setTimeout(() => {
        this.loading = false;
        this.submitted = true;
      }, 1800);
    },
  },
};
</script>

<style scoped>

/* ─── Section ───────────────────────────────────── */
.contact {
  position: relative;
  padding-block: var(--section-pad);
  background: var(--grey-950);
  overflow: hidden;
}

/* ─── Background ────────────────────────────────── */
.contact__bg { position: absolute; inset: 0; pointer-events: none; }

.contact__bg-glow {
  position: absolute;
  left: 0; top: 50%;
  transform: translateY(-50%);
  width: 600px; height: 600px;
  background: radial-gradient(circle, rgba(255,107,91,0.07) 0%, transparent 65%);
  border-radius: 50%;
}

.contact__bg-grid {
  position: absolute;
  inset: 0;
  background-image: radial-gradient(rgba(255,255,255,0.03) 1px, transparent 1px);
  background-size: 36px 36px;
  mask-image: radial-gradient(ellipse 80% 80% at 50% 50%, black, transparent);
}

.contact__bg-lines {
  position: absolute;
  inset: 0;
  background-image: linear-gradient(rgba(255,255,255,0.02) 1px, transparent 1px);
  background-size: 100% 80px;
}

/* ─── Container ─────────────────────────────────── */
.contact__container {
  position: relative;
  z-index: 1;
  max-width: var(--max-width);
  margin: 0 auto;
  padding-inline: clamp(24px, 5vw, 80px);
  display: grid;
  grid-template-columns: 1fr 1.1fr;
  gap: clamp(48px, 7vw, 100px);
  align-items: start;
}

/* ─── LEFT ──────────────────────────────────────── */
.contact__left {
  padding-top: 12px;
  position: sticky;
  top: calc(var(--nav-height) + 32px);
}

.contact__eyebrow {
  display: flex;
  align-items: center;
  gap: 12px;
  font-size: var(--text-xs);
  font-weight: 500;
  letter-spacing: 0.22em;
  text-transform: uppercase;
  color: var(--coral);
  margin-bottom: 20px;
}

.contact__eyebrow-line {
  display: block;
  width: 32px;
  height: 1px;
  background: var(--coral);
  flex-shrink: 0;
}

.contact__heading {
  display: flex;
  flex-direction: column;
  gap: 2px;
  font-family: var(--font-display);
  font-size: clamp(2.2rem, 3.8vw, 3.4rem);
  font-weight: 700;
  line-height: 1.1;
  letter-spacing: -0.02em;
  margin-bottom: 20px;
}

.contact__heading-line       { color: var(--white); }
.contact__heading-line--ghost {
  color: transparent;
  -webkit-text-stroke: 1.5px rgba(255,255,255,0.2);
}
.contact__heading-line--coral { color: var(--coral); }

.contact__sub {
  font-size: 0.88rem;
  line-height: 1.85;
  color: var(--grey-400);
  margin-bottom: 40px;
  max-width: 380px;
}

/* Contact details */
.contact__details {
  list-style: none;
  display: flex;
  flex-direction: column;
  gap: 20px;
  margin-bottom: 40px;
}

.contact__detail {
  display: flex;
  align-items: flex-start;
  gap: 16px;
}

.contact__detail-icon {
  display: flex;
  align-items: center;
  justify-content: center;
  width: 40px;
  height: 40px;
  border-radius: 8px;
  background: rgba(255,107,91,0.08);
  border: 1px solid rgba(255,107,91,0.14);
  flex-shrink: 0;
  margin-top: 2px;
  transition: background 0.25s, border-color 0.25s;
}

.contact__detail:hover .contact__detail-icon {
  background: rgba(255,107,91,0.14);
  border-color: rgba(255,107,91,0.28);
}

.contact__detail-label {
  display: block;
  font-size: 0.62rem;
  letter-spacing: 0.18em;
  text-transform: uppercase;
  color: rgba(255,255,255,0.3);
  margin-bottom: 3px;
}

.contact__detail-value {
  font-size: 0.85rem;
  color: var(--white);
  text-decoration: none;
  font-weight: 500;
  transition: color 0.22s;
}

.contact__detail-value:hover { color: var(--coral); }

/* Offices */
.contact__offices { }

.contact__offices-label {
  display: block;
  font-size: 0.62rem;
  letter-spacing: 0.2em;
  text-transform: uppercase;
  color: rgba(255,255,255,0.25);
  margin-bottom: 16px;
}

.contact__offices-list {
  display: flex;
  flex-direction: column;
  gap: 14px;
}

.contact__office {
  display: flex;
  align-items: flex-start;
  gap: 12px;
}

.contact__office-dot {
  width: 6px;
  height: 6px;
  border-radius: 50%;
  background: var(--coral);
  flex-shrink: 0;
  margin-top: 6px;
  opacity: 0.6;
}

.contact__office-city {
  font-size: 0.8rem;
  font-weight: 600;
  color: var(--white);
  line-height: 1.3;
}

.contact__office-addr {
  font-size: 0.72rem;
  color: var(--grey-400);
  margin-top: 1px;
}

/* ─── RIGHT — Form Card ─────────────────────────── */
.contact__right { }

.contact__form-card {
  background: rgba(255,255,255,0.03);
  border: 1px solid rgba(255,255,255,0.07);
  border-radius: 16px;
  overflow: hidden;
  box-shadow: 0 32px 80px rgba(0,0,0,0.35);
}

.contact__form-header {
  display: flex;
  flex-direction: column;
  gap: 4px;
  padding: 28px 32px 24px;
  border-bottom: 1px solid rgba(255,255,255,0.06);
  background: rgba(255,107,91,0.04);
}

.contact__form-title {
  font-family: var(--font-display);
  font-size: 1.15rem;
  font-weight: 700;
  color: var(--white);
}

.contact__form-sub {
  font-size: 0.72rem;
  letter-spacing: 0.1em;
  color: var(--coral);
  text-transform: uppercase;
}

.contact__form {
  padding: 28px 32px 32px;
  display: flex;
  flex-direction: column;
  gap: 20px;
}

/* Row */
.contact__form-row {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 16px;
}

/* Field */
.contact__field {
  display: flex;
  flex-direction: column;
  gap: 6px;
}

.contact__label {
  font-size: 0.68rem;
  font-weight: 500;
  letter-spacing: 0.12em;
  text-transform: uppercase;
  color: rgba(255,255,255,0.45);
}

.contact__label-opt {
  color: rgba(255,255,255,0.2);
  font-weight: 400;
  text-transform: none;
  letter-spacing: 0;
}

/* Input wrap */
.contact__input-wrap {
  position: relative;
}

.contact__input {
  width: 100%;
  background: rgba(255,255,255,0.04);
  border: 1px solid rgba(255,255,255,0.09);
  border-radius: 6px;
  padding: 12px 14px;
  color: var(--white);
  font-size: 0.85rem;
  font-family: var(--font-body);
  transition: border-color 0.25s, background 0.25s;
  appearance: none;
  -webkit-appearance: none;
}

.contact__input::placeholder { color: rgba(255,255,255,0.2); }

.contact__input:focus {
  outline: none;
  border-color: rgba(255,107,91,0.5);
  background: rgba(255,107,91,0.04);
}

/* Animated bottom line on focus */
.contact__input-line {
  position: absolute;
  bottom: 0; left: 50%;
  width: 0; height: 1.5px;
  background: var(--coral);
  border-radius: 2px;
  transform: translateX(-50%);
  transition: width 0.35s var(--ease);
  pointer-events: none;
}

.contact__input:focus ~ .contact__input-line {
  width: calc(100% - 12px);
}

/* Select */
.contact__input-wrap--select { position: relative; }

.contact__select {
  cursor: pointer;
  padding-right: 36px;
  color: var(--white);
}

.contact__select option {
  background: var(--grey-800);
  color: var(--white);
}

.contact__select-arrow {
  position: absolute;
  right: 12px;
  top: 50%;
  transform: translateY(-50%);
  color: rgba(255,255,255,0.3);
  pointer-events: none;
  display: flex;
  align-items: center;
}

/* Error */
.contact__field--error .contact__input {
  border-color: rgba(248,113,113,0.5);
}

.contact__error {
  font-size: 0.65rem;
  color: #f87171;
  letter-spacing: 0.05em;
}

/* Interests */
.contact__interests {
  display: flex;
  flex-wrap: wrap;
  gap: 8px;
}

.contact__interest-btn {
  padding: 7px 14px;
  font-size: 0.7rem;
  font-weight: 400;
  letter-spacing: 0.08em;
  text-transform: uppercase;
  color: rgba(255,255,255,0.45);
  background: rgba(255,255,255,0.04);
  border: 1px solid rgba(255,255,255,0.09);
  border-radius: 3px;
  cursor: pointer;
  transition: all 0.22s var(--ease);
}

.contact__interest-btn:hover {
  color: var(--white);
  border-color: rgba(255,255,255,0.2);
}

.contact__interest-btn--active {
  color: var(--coral);
  border-color: rgba(255,107,91,0.4);
  background: rgba(255,107,91,0.08);
}

/* Textarea */
.contact__textarea {
  resize: vertical;
  min-height: 80px;
}

/* Submit */
.contact__submit {
  width: 100%;
  padding: 15px 28px;
  background: var(--coral);
  color: var(--white);
  border: none;
  border-radius: 6px;
  font-family: var(--font-body);
  font-size: 0.82rem;
  font-weight: 500;
  letter-spacing: 0.1em;
  text-transform: uppercase;
  cursor: pointer;
  box-shadow: 0 4px 24px rgba(255,107,91,0.28);
  transition: background 0.28s, transform 0.28s var(--ease), box-shadow 0.28s;
  min-height: 50px;
  display: flex;
  align-items: center;
  justify-content: center;
}

.contact__submit:hover:not(.contact__submit--loading):not(.contact__submit--done) {
  background: var(--coral-dark);
  box-shadow: 0 8px 32px rgba(255,107,91,0.4);
  transform: translateY(-2px);
}

.contact__submit--done {
  background: rgba(74,222,128,0.15);
  border: 1px solid rgba(74,222,128,0.3);
  color: #4ade80;
  box-shadow: none;
  cursor: default;
}

.contact__submit-inner {
  display: flex;
  align-items: center;
  gap: 10px;
}

.contact__submit-inner svg {
  transition: transform 0.25s var(--ease);
}

.contact__submit:hover .contact__submit-inner svg {
  transform: translateX(4px);
}

.contact__submit-success {
  letter-spacing: 0.08em;
}

/* Spinner */
.contact__spinner {
  display: inline-block;
  width: 18px; height: 18px;
  border: 2px solid rgba(255,255,255,0.3);
  border-top-color: var(--white);
  border-radius: 50%;
  animation: spin 0.7s linear infinite;
}

@keyframes spin { to { transform: rotate(360deg); } }

.contact__form-note {
  font-size: 0.65rem;
  color: rgba(255,255,255,0.2);
  text-align: center;
  line-height: 1.6;
  letter-spacing: 0.03em;
}

/* ─── Responsive ────────────────────────────────── */
@media (max-width: 1024px) {
  .contact__container {
    grid-template-columns: 1fr;
    gap: 56px;
  }

  .contact__left {
    position: static;
  }
}

@media (max-width: 540px) {
  .contact__form-row {
    grid-template-columns: 1fr;
  }

  .contact__form-card {
    border-radius: 12px;
  }

  .contact__form {
    padding: 20px 20px 24px;
  }

  .contact__form-header {
    padding: 20px 20px 16px;
  }
}
</style>