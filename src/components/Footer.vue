<template>
  <footer class="footer">

    <!-- Top accent line -->
    <div class="footer__accent-line"></div>

    <!-- Background -->
    <div class="footer__bg" aria-hidden="true">
      <div class="footer__bg-glow"></div>
      <div class="footer__bg-grid"></div>
    </div>

    <div class="footer__container">

      <!-- ── TOP ROW ── -->
      <div class="footer__top">

        <!-- Brand col -->
        <div class="footer__brand">
          <a href="#home" class="footer__logo">
            <span class="footer__logo-mark">
              <svg width="36" height="36" viewBox="0 0 32 32" fill="none">
                <polygon class="footer__logo-poly" points="16,2 30,10 30,22 16,30 2,22 2,10" stroke="#FF6B5B" stroke-width="2" fill="none"/>
                <polygon points="16,8 24,13 24,19 16,24 8,19 8,13" fill="#FF6B5B" opacity="0.12"/>
                <line x1="16" y1="2" x2="16" y2="30" stroke="#FF6B5B" stroke-width="1" opacity="0.35"/>
                <line x1="2" y1="10" x2="30" y2="22" stroke="#FF6B5B" stroke-width="1" opacity="0.35"/>
                <line x1="30" y1="10" x2="2" y2="22" stroke="#FF6B5B" stroke-width="1" opacity="0.35"/>
              </svg>
            </span>
            <span class="footer__logo-text">
              <span class="footer__logo-name">Harderlin</span>
              <span class="footer__logo-sub">Investment Group</span>
            </span>
          </a>

          <p class="footer__brand-desc">
            Building enduring wealth through disciplined strategy,
            deep research, and unwavering client alignment since 2004.
          </p>

          <!-- Social links -->
          <div class="footer__socials">
            <a
              v-for="social in socials"
              :key="social.label"
              :href="social.href"
              :aria-label="social.label"
              class="footer__social"
            >
              <span v-html="social.icon"></span>
            </a>
          </div>
        </div>

        <!-- Nav columns -->
        <div
          v-for="col in navCols"
          :key="col.heading"
          class="footer__nav-col"
        >
          <h4 class="footer__nav-heading">{{ col.heading }}</h4>
          <ul class="footer__nav-list">
            <li v-for="link in col.links" :key="link.label">
              <a :href="link.href" class="footer__nav-link">
                <span class="footer__nav-link-arrow">›</span>
                {{ link.label }}
              </a>
            </li>
          </ul>
        </div>

        <!-- Newsletter col -->
        <div class="footer__newsletter">
          <h4 class="footer__nav-heading">Market Insights</h4>
          <p class="footer__newsletter-desc">
            Weekly macro commentary and investment analysis delivered to your inbox.
          </p>
          <form class="footer__newsletter-form" @submit.prevent="subscribeNewsletter">
            <div class="footer__newsletter-input-wrap">
              <input
                v-model="newsletterEmail"
                type="email"
                placeholder="your@email.com"
                class="footer__newsletter-input"
                :disabled="newsletterDone"
              />
              <button
                type="submit"
                class="footer__newsletter-btn"
                :class="{ 'footer__newsletter-btn--done': newsletterDone }"
                :disabled="newsletterDone"
              >
                <span v-if="!newsletterDone">
                  <svg width="14" height="14" viewBox="0 0 14 14" fill="none">
                    <path d="M2 7h10M8 3l4 4-4 4" stroke="currentColor" stroke-width="1.4" stroke-linecap="round" stroke-linejoin="round"/>
                  </svg>
                </span>
                <span v-else>✓</span>
              </button>
            </div>
            <p v-if="newsletterDone" class="footer__newsletter-success">
              You're subscribed. Welcome aboard.
            </p>
          </form>

          <!-- Certifications -->
          <div class="footer__certs">
            <span v-for="cert in certs" :key="cert" class="footer__cert">{{ cert }}</span>
          </div>
        </div>

      </div>

      <!-- ── DIVIDER ── -->
      <div class="footer__divider"></div>

      <!-- ── STATS BAR ── -->
      <div class="footer__stats-bar">
        <div v-for="(stat, i) in stats" :key="stat.label" class="footer__stat">
          <span class="footer__stat-value">{{ stat.value }}</span>
          <span class="footer__stat-label">{{ stat.label }}</span>
          <span v-if="i < stats.length - 1" class="footer__stat-sep" aria-hidden="true">—</span>
        </div>
      </div>

      <!-- ── DIVIDER ── -->
      <div class="footer__divider"></div>

      <!-- ── BOTTOM ROW ── -->
      <div class="footer__bottom">
        <div class="footer__bottom-left">
          <span class="footer__copy">
            © {{ year }} Harderlin Investment Group. All rights reserved.
          </span>
          <span class="footer__reg">
            Registered investment advisor. Securities offered through Harderlin Capital LLC.
          </span>
        </div>

        <div class="footer__bottom-links">
          <a v-for="link in legalLinks" :key="link" href="#" class="footer__legal-link">
            {{ link }}
          </a>
        </div>

        <a href="#home" class="footer__back-top" @click.prevent="scrollToTop" aria-label="Back to top">
          <svg width="16" height="16" viewBox="0 0 16 16" fill="none">
            <path d="M8 13V3M4 7l4-4 4 4" stroke="currentColor" stroke-width="1.4" stroke-linecap="round" stroke-linejoin="round"/>
          </svg>
        </a>
      </div>

    </div>

  </footer>
</template>

<script>
export default {
  name: 'Footer',
  data() {
    return {
      newsletterEmail: '',
      newsletterDone: false,
      year: new Date().getFullYear(),
      stats: [
        { value: '$4.2B+',  label: 'Assets Under Management' },
        { value: '2,400+',  label: 'Clients Worldwide' },
        { value: '19yr',    label: 'Years in Operation' },
        { value: '60+',     label: 'Investment Professionals' },
        { value: '3',       label: 'Global Offices' },
      ],
      certs: ['SEC Registered', 'FCA Authorised', 'MAS Licensed'],
      legalLinks: ['Privacy Policy', 'Terms of Use', 'Disclosures', 'Cookie Policy'],
      socials: [
        {
          label: 'LinkedIn',
          href: '#',
          icon: `<svg width="16" height="16" viewBox="0 0 24 24" fill="none">
                   <path d="M16 8a6 6 0 016 6v7h-4v-7a2 2 0 00-2-2 2 2 0 00-2 2v7h-4v-7a6 6 0 016-6zM2 9h4v12H2z" stroke="currentColor" stroke-width="1.5" stroke-linejoin="round"/>
                   <circle cx="4" cy="4" r="2" stroke="currentColor" stroke-width="1.5"/>
                 </svg>`,
        },
        {
          label: 'Twitter / X',
          href: '#',
          icon: `<svg width="16" height="16" viewBox="0 0 24 24" fill="none">
                   <path d="M4 4l16 16M4 20L20 4" stroke="currentColor" stroke-width="1.6" stroke-linecap="round"/>
                 </svg>`,
        },
        {
          label: 'Bloomberg',
          href: '#',
          icon: `<svg width="16" height="16" viewBox="0 0 24 24" fill="none">
                   <rect x="3" y="3" width="18" height="18" rx="3" stroke="currentColor" stroke-width="1.5"/>
                   <path d="M8 12h4M8 8h8M8 16h6" stroke="currentColor" stroke-width="1.5" stroke-linecap="round"/>
                 </svg>`,
        },
        {
          label: 'Email',
          href: 'mailto:advisory@harderlin.com',
          icon: `<svg width="16" height="16" viewBox="0 0 24 24" fill="none">
                   <rect x="3" y="5" width="18" height="14" rx="2" stroke="currentColor" stroke-width="1.5"/>
                   <path d="M3 8l9 6 9-6" stroke="currentColor" stroke-width="1.5" stroke-linecap="round"/>
                 </svg>`,
        },
      ],
      navCols: [
        {
          heading: 'Company',
          links: [
            { label: 'About Us',       href: '#about'    },
            { label: 'Leadership',     href: '#about'    },
            { label: 'Careers',        href: '#'         },
            { label: 'Press',          href: '#'         },
            { label: 'Sustainability', href: '#'         },
          ],
        },
        {
          heading: 'Services',
          links: [
            { label: 'Wealth Management', href: '#services' },
            { label: 'Private Equity',    href: '#services' },
            { label: 'Fixed Income',      href: '#services' },
            { label: 'Global Markets',    href: '#services' },
            { label: 'Alternatives',      href: '#services' },
          ],
        },
        {
          heading: 'Resources',
          links: [
            { label: 'Insights',       href: '#insights' },
            { label: 'Market Reports', href: '#'         },
            { label: 'Webinars',       href: '#'         },
            { label: 'FAQ',            href: '#'         },
            { label: 'Contact',        href: '#contact'  },
          ],
        },
      ],
    };
  },
  methods: {
    subscribeNewsletter() {
      if (!this.newsletterEmail) return;
      this.newsletterDone = true;
    },
    scrollToTop() {
      window.scrollTo({ top: 0, behavior: 'smooth' });
    },
  },
};
</script>

<style scoped>

/* ─── Footer shell ──────────────────────────────── */
.footer {
  position: relative;
  background: var(--black);
  overflow: hidden;
  font-family: var(--font-body);
}

/* ─── Accent line ───────────────────────────────── */
.footer__accent-line {
  height: 1px;
  background: linear-gradient(90deg, transparent, rgba(255,107,91,0.35) 40%, rgba(255,107,91,0.35) 60%, transparent);
}

/* ─── Background ────────────────────────────────── */
.footer__bg { position: absolute; inset: 0; pointer-events: none; }

.footer__bg-glow {
  position: absolute;
  left: 50%; bottom: -100px;
  transform: translateX(-50%);
  width: 700px; height: 400px;
  background: radial-gradient(ellipse, rgba(255,107,91,0.06) 0%, transparent 65%);
}

.footer__bg-grid {
  position: absolute;
  inset: 0;
  background-image: radial-gradient(rgba(255,255,255,0.025) 1px, transparent 1px);
  background-size: 40px 40px;
  mask-image: radial-gradient(ellipse 100% 80% at 50% 100%, black, transparent);
}

/* ─── Container ─────────────────────────────────── */
.footer__container {
  position: relative;
  z-index: 1;
  max-width: var(--max-width);
  margin: 0 auto;
  padding: clamp(56px, 8vw, 96px) clamp(24px, 5vw, 80px) clamp(32px, 5vw, 48px);
}

/* ─── Top Row ───────────────────────────────────── */
.footer__top {
  display: grid;
  grid-template-columns: 1.4fr 1fr 1fr 1fr 1.3fr;
  gap: 40px;
  margin-bottom: 48px;
}

/* ─── Brand col ─────────────────────────────────── */
.footer__logo {
  display: inline-flex;
  align-items: center;
  gap: 12px;
  text-decoration: none;
  margin-bottom: 20px;
}

.footer__logo-mark svg {
  transition: transform 0.5s var(--ease);
}
.footer__logo:hover .footer__logo-mark svg {
  transform: rotate(30deg) scale(1.06);
}

.footer__logo-poly {
  stroke-dasharray: 120;
  stroke-dashoffset: 0;
}

.footer__logo-text {
  display: flex;
  flex-direction: column;
  line-height: 1;
}
.footer__logo-name {
  font-family: var(--font-display);
  font-size: 1.3rem;
  font-weight: 700;
  letter-spacing: 0.04em;
  color: var(--white);
  text-transform: uppercase;
}
.footer__logo-sub {
  font-size: 0.55rem;
  font-weight: 300;
  letter-spacing: 0.22em;
  color: var(--coral);
  text-transform: uppercase;
  margin-top: 2px;
}

.footer__brand-desc {
  font-size: 0.82rem;
  line-height: 1.8;
  color: var(--grey-400);
  margin-bottom: 24px;
  max-width: 280px;
}

/* Socials */
.footer__socials {
  display: flex;
  gap: 8px;
}

.footer__social {
  display: flex;
  align-items: center;
  justify-content: center;
  width: 36px; height: 36px;
  border-radius: 6px;
  border: 1px solid rgba(255,255,255,0.08);
  color: rgba(255,255,255,0.4);
  text-decoration: none;
  transition: color 0.25s, border-color 0.25s, background 0.25s, transform 0.25s var(--ease);
}

.footer__social:hover {
  color: var(--white);
  border-color: rgba(255,107,91,0.4);
  background: rgba(255,107,91,0.08);
  transform: translateY(-3px);
}

/* ─── Nav cols ──────────────────────────────────── */
.footer__nav-heading {
  font-family: var(--font-body);
  font-size: 0.65rem;
  font-weight: 600;
  letter-spacing: 0.22em;
  text-transform: uppercase;
  color: rgba(255,255,255,0.35);
  margin-bottom: 18px;
}

.footer__nav-list {
  list-style: none;
  display: flex;
  flex-direction: column;
  gap: 10px;
}

.footer__nav-link {
  display: flex;
  align-items: center;
  gap: 0;
  font-size: 0.82rem;
  color: var(--grey-400);
  text-decoration: none;
  transition: color 0.22s var(--ease), gap 0.22s var(--ease), padding-left 0.22s var(--ease);
}

.footer__nav-link-arrow {
  color: var(--coral);
  opacity: 0;
  font-size: 0.9rem;
  transform: translateX(-4px);
  transition: opacity 0.2s, transform 0.2s var(--ease);
  flex-shrink: 0;
  line-height: 1;
}

.footer__nav-link:hover {
  color: var(--white);
  gap: 6px;
}

.footer__nav-link:hover .footer__nav-link-arrow {
  opacity: 1;
  transform: translateX(0);
}

/* ─── Newsletter col ────────────────────────────── */
.footer__newsletter-desc {
  font-size: 0.78rem;
  line-height: 1.7;
  color: var(--grey-400);
  margin-bottom: 16px;
}

.footer__newsletter-form { margin-bottom: 20px; }

.footer__newsletter-input-wrap {
  display: flex;
  align-items: center;
  background: rgba(255,255,255,0.04);
  border: 1px solid rgba(255,255,255,0.09);
  border-radius: 6px;
  overflow: hidden;
  transition: border-color 0.25s;
}

.footer__newsletter-input-wrap:focus-within {
  border-color: rgba(255,107,91,0.45);
}

.footer__newsletter-input {
  flex: 1;
  background: none;
  border: none;
  padding: 11px 14px;
  color: var(--white);
  font-size: 0.8rem;
  font-family: var(--font-body);
  outline: none;
}

.footer__newsletter-input::placeholder { color: rgba(255,255,255,0.22); }
.footer__newsletter-input:disabled { opacity: 0.5; }

.footer__newsletter-btn {
  display: flex;
  align-items: center;
  justify-content: center;
  width: 40px; height: 40px;
  background: var(--coral);
  border: none;
  color: var(--white);
  cursor: pointer;
  flex-shrink: 0;
  transition: background 0.25s;
}

.footer__newsletter-btn:hover { background: var(--coral-dark); }
.footer__newsletter-btn--done { background: rgba(74,222,128,0.2); color: #4ade80; cursor: default; }

.footer__newsletter-success {
  font-size: 0.68rem;
  color: #4ade80;
  letter-spacing: 0.08em;
  margin-top: 8px;
}

/* Certs */
.footer__certs {
  display: flex;
  flex-direction: column;
  gap: 6px;
  margin-top: 4px;
}

.footer__cert {
  font-size: 0.6rem;
  letter-spacing: 0.14em;
  text-transform: uppercase;
  color: rgba(255,255,255,0.2);
  display: flex;
  align-items: center;
  gap: 6px;
}

.footer__cert::before {
  content: '';
  display: block;
  width: 4px; height: 4px;
  border-radius: 50%;
  background: rgba(255,107,91,0.4);
  flex-shrink: 0;
}

/* ─── Divider ───────────────────────────────────── */
.footer__divider {
  height: 1px;
  background: linear-gradient(90deg, transparent, rgba(255,255,255,0.06) 20%, rgba(255,255,255,0.06) 80%, transparent);
  margin-block: 32px;
}

/* ─── Stats bar ─────────────────────────────────── */
.footer__stats-bar {
  display: flex;
  align-items: center;
  justify-content: center;
  gap: 0;
  flex-wrap: wrap;
  row-gap: 16px;
}

.footer__stat {
  display: flex;
  align-items: center;
  gap: 12px;
  padding: 0 32px;
  border-right: 1px solid rgba(255,255,255,0.06);
  text-align: center;
  flex-direction: column;
  gap: 2px;
}

.footer__stat:last-child { border-right: none; }

.footer__stat-value {
  font-family: var(--font-display);
  font-size: 1.6rem;
  font-weight: 700;
  color: var(--white);
  letter-spacing: -0.02em;
  line-height: 1;
}

.footer__stat-label {
  font-size: 0.62rem;
  letter-spacing: 0.14em;
  text-transform: uppercase;
  color: var(--grey-400);
}

.footer__stat-sep { display: none; }

/* ─── Bottom row ────────────────────────────────── */
.footer__bottom {
  display: flex;
  align-items: center;
  justify-content: space-between;
  gap: 24px;
  flex-wrap: wrap;
}

.footer__bottom-left {
  display: flex;
  flex-direction: column;
  gap: 4px;
}

.footer__copy {
  font-size: 0.75rem;
  color: rgba(255,255,255,0.3);
  letter-spacing: 0.04em;
}

.footer__reg {
  font-size: 0.62rem;
  color: rgba(255,255,255,0.15);
  letter-spacing: 0.04em;
  max-width: 420px;
}

.footer__bottom-links {
  display: flex;
  gap: 20px;
  flex-wrap: wrap;
}

.footer__legal-link {
  font-size: 0.7rem;
  color: rgba(255,255,255,0.25);
  text-decoration: none;
  letter-spacing: 0.06em;
  transition: color 0.22s;
}

.footer__legal-link:hover { color: var(--coral); }

/* Back to top */
.footer__back-top {
  display: flex;
  align-items: center;
  justify-content: center;
  width: 38px; height: 38px;
  border: 1px solid rgba(255,255,255,0.1);
  border-radius: 6px;
  color: rgba(255,255,255,0.35);
  text-decoration: none;
  flex-shrink: 0;
  transition: color 0.25s, border-color 0.25s, background 0.25s, transform 0.3s var(--ease);
}

.footer__back-top:hover {
  color: var(--white);
  border-color: rgba(255,107,91,0.45);
  background: rgba(255,107,91,0.08);
  transform: translateY(-3px);
}

/* ─── Responsive ────────────────────────────────── */
@media (max-width: 1100px) {
  .footer__top {
    grid-template-columns: 1fr 1fr 1fr;
  }

  .footer__brand {
    grid-column: 1 / -1;
    display: grid;
    grid-template-columns: auto 1fr auto;
    align-items: start;
    gap: 32px;
  }

  .footer__logo { margin-bottom: 0; }
  .footer__brand-desc { margin-bottom: 0; }
}

@media (max-width: 768px) {
  .footer__top {
    grid-template-columns: 1fr 1fr;
  }

  .footer__brand {
    grid-column: 1 / -1;
    display: flex;
    flex-direction: column;
    gap: 16px;
  }

  .footer__stats-bar {
    justify-content: flex-start;
    gap: 16px;
  }

  .footer__stat {
    padding: 0 16px;
    flex-direction: row;
    gap: 8px;
    border-right: none;
    border-bottom: 1px solid rgba(255,255,255,0.06);
    padding-bottom: 12px;
    width: 100%;
    justify-content: flex-start;
    align-items: baseline;
  }

  .footer__stat:last-child { border-bottom: none; }
}

@media (max-width: 540px) {
  .footer__top { grid-template-columns: 1fr; }

  .footer__bottom {
    flex-direction: column;
    align-items: flex-start;
    gap: 16px;
  }

  .footer__back-top {
    align-self: flex-end;
  }
}
</style>