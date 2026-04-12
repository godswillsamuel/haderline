<template>
  <section id="services" class="services">

    <!-- Background -->
    <div class="services__bg" aria-hidden="true">
      <div class="services__bg-grid"></div>
      <div class="services__bg-glow"></div>
    </div>

    <div class="services__container">

      <!-- Section Header -->
      <div class="services__header" ref="header">
        <div class="services__eyebrow">
          <span class="services__eyebrow-line"></span>
          <span>What We Offer</span>
        </div>
        <h2 class="services__heading">
          <span class="services__heading-line">Strategic Services</span>
          <span class="services__heading-line services__heading-line--ghost">Built for Growth.</span>
        </h2>
        <p class="services__heading-sub">
          From private equity to structured wealth planning, Harderlin delivers
          institutional-grade investment solutions tailored to every stage of your journey.
        </p>
      </div>

      <!-- Services Grid -->
      <div class="services__grid">
        <div
          v-for="(service, i) in services"
          :key="service.title"
          class="services__card"
          :class="{ 'services__card--featured': service.featured }"
          :style="`--ci: ${i}`"
          @mouseenter="hovered = i"
          @mouseleave="hovered = null"
        >
          <!-- Card number -->
          <span class="services__card-num">0{{ i + 1 }}</span>

          <!-- Icon -->
          <div class="services__icon-wrap">
            <span class="services__icon" v-html="service.icon"></span>
            <span class="services__icon-bg"></span>
          </div>

          <!-- Content -->
          <h3 class="services__card-title">{{ service.title }}</h3>
          <p class="services__card-desc">{{ service.desc }}</p>

          <!-- Tags -->
          <ul class="services__tags">
            <li v-for="tag in service.tags" :key="tag" class="services__tag">{{ tag }}</li>
          </ul>

          <!-- Arrow -->
          <div class="services__card-arrow">
            <svg width="18" height="18" viewBox="0 0 18 18" fill="none">
              <path d="M3 9h12M10 4l5 5-5 5" stroke="currentColor" stroke-width="1.5" stroke-linecap="round" stroke-linejoin="round"/>
            </svg>
          </div>

          <!-- Hover border glow -->
          <span class="services__card-glow"></span>
        </div>
      </div>

      <!-- Bottom CTA strip -->
      <div class="services__cta-strip">
        <div class="services__cta-strip-left">
          <span class="services__cta-strip-label">Ready to start?</span>
          <p class="services__cta-strip-text">
            Schedule a complimentary consultation with one of our senior advisors.
          </p>
        </div>
        <a href="#contact" class="services__cta-btn">
          <span>Book a Consultation</span>
          <svg width="16" height="16" viewBox="0 0 16 16" fill="none">
            <path d="M3 8h10M9 4l4 4-4 4" stroke="currentColor" stroke-width="1.4" stroke-linecap="round" stroke-linejoin="round"/>
          </svg>
        </a>
      </div>

    </div>
  </section>
</template>

<script>
export default {
  name: 'ServicesSection',
  data() {
    return {
      hovered: null,
      services: [
        {
          title: 'Wealth Management',
          desc: 'Personalised strategies that preserve and grow your wealth across market cycles with disciplined risk management.',
          icon: `<svg width="28" height="28" viewBox="0 0 28 28" fill="none">
                   <circle cx="14" cy="14" r="11" stroke="#FF6B5B" stroke-width="1.5"/>
                   <path d="M14 8v6l4 2" stroke="#FF6B5B" stroke-width="1.5" stroke-linecap="round"/>
                   <path d="M9 19l3-3" stroke="#FF6B5B" stroke-width="1.2" stroke-linecap="round" opacity="0.5"/>
                 </svg>`,
          tags: ['Private Clients', 'HNW Families', 'Estate Planning'],
          featured: false,
        },
        {
          title: 'Private Equity',
          desc: 'Exclusive access to high-conviction private market opportunities — from growth-stage ventures to established buyouts.',
          icon: `<svg width="28" height="28" viewBox="0 0 28 28" fill="none">
                   <rect x="4" y="16" width="5" height="8" rx="1" stroke="#FF6B5B" stroke-width="1.5"/>
                   <rect x="11.5" y="10" width="5" height="14" rx="1" stroke="#FF6B5B" stroke-width="1.5"/>
                   <rect x="19" y="5" width="5" height="19" rx="1" stroke="#FF6B5B" stroke-width="1.5"/>
                   <path d="M4 13l7-6 7 4 6-7" stroke="#FF6B5B" stroke-width="1.2" stroke-linecap="round" opacity="0.45"/>
                 </svg>`,
          tags: ['Venture', 'Buyouts', 'Co-investments'],
          featured: true,
        },
        {
          title: 'Fixed Income',
          desc: 'Structured bond portfolios and income strategies designed to deliver consistent returns with capital preservation.',
          icon: `<svg width="28" height="28" viewBox="0 0 28 28" fill="none">
                   <path d="M6 22 C8 14 12 18 14 12 C16 6 20 10 22 6" stroke="#FF6B5B" stroke-width="1.5" stroke-linecap="round"/>
                   <circle cx="22" cy="6" r="2.5" stroke="#FF6B5B" stroke-width="1.5"/>
                   <path d="M6 18h16" stroke="#FF6B5B" stroke-width="1" opacity="0.3" stroke-dasharray="2 3"/>
                 </svg>`,
          tags: ['Government Bonds', 'Credit', 'Duration'],
          featured: false,
        },
        {
          title: 'Retirement Planning',
          desc: 'Forward-looking pension and retirement strategies that ensure financial independence throughout your lifetime.',
          icon: `<svg width="28" height="28" viewBox="0 0 28 28" fill="none">
                   <path d="M14 4 C9 4 5 8 5 13 C5 18 9 22 14 22 C19 22 23 18 23 13" stroke="#FF6B5B" stroke-width="1.5" stroke-linecap="round"/>
                   <path d="M18 4l5 0 0 5" stroke="#FF6B5B" stroke-width="1.5" stroke-linecap="round" stroke-linejoin="round"/>
                   <path d="M14 9v5l3 2" stroke="#FF6B5B" stroke-width="1.4" stroke-linecap="round"/>
                 </svg>`,
          tags: ['Pension Funds', 'Annuities', 'Life Planning'],
          featured: false,
        },
        {
          title: 'Global Markets',
          desc: 'Active exposure to equities, commodities, and currencies across developed and emerging markets worldwide.',
          icon: `<svg width="28" height="28" viewBox="0 0 28 28" fill="none">
                   <circle cx="14" cy="14" r="10" stroke="#FF6B5B" stroke-width="1.5"/>
                   <ellipse cx="14" cy="14" rx="4" ry="10" stroke="#FF6B5B" stroke-width="1.2" opacity="0.5"/>
                   <path d="M4 14h20" stroke="#FF6B5B" stroke-width="1.2" opacity="0.4"/>
                   <path d="M6 9h16M6 19h16" stroke="#FF6B5B" stroke-width="1" opacity="0.25"/>
                 </svg>`,
          tags: ['Equities', 'Commodities', 'FX'],
          featured: false,
        },
        {
          title: 'Alternative Assets',
          desc: 'Diversify beyond traditional markets with real estate, infrastructure, hedge funds, and digital assets.',
          icon: `<svg width="28" height="28" viewBox="0 0 28 28" fill="none">
                   <polygon points="14,3 25,9 25,21 14,27 3,21 3,9" stroke="#FF6B5B" stroke-width="1.5" fill="none"/>
                   <polygon points="14,9 20,12 20,18 14,21 8,18 8,12" stroke="#FF6B5B" stroke-width="1" fill="none" opacity="0.4"/>
                   <circle cx="14" cy="15" r="2" fill="#FF6B5B" opacity="0.6"/>
                 </svg>`,
          tags: ['Real Estate', 'Hedge Funds', 'Digital Assets'],
          featured: false,
        },
      ],
    };
  },
};
</script>

<style scoped>

/* ─── Section ───────────────────────────────────── */
.services {
  position: relative;
  padding-block: var(--section-pad);
  background: var(--grey-900);
  overflow: hidden;
}

/* ─── Background ────────────────────────────────── */
.services__bg {
  position: absolute;
  inset: 0;
  pointer-events: none;
}

.services__bg-grid {
  position: absolute;
  inset: 0;
  background-image: radial-gradient(rgba(255,255,255,0.03) 1px, transparent 1px);
  background-size: 40px 40px;
  mask-image: radial-gradient(ellipse 80% 80% at 50% 50%, black, transparent);
}

.services__bg-glow {
  position: absolute;
  left: -15%;
  top: 30%;
  width: 600px;
  height: 600px;
  background: radial-gradient(circle, rgba(255,107,91,0.06) 0%, transparent 65%);
  border-radius: 50%;
}

/* ─── Container ─────────────────────────────────── */
.services__container {
  position: relative;
  z-index: 1;
  max-width: var(--max-width);
  margin: 0 auto;
  padding-inline: clamp(24px, 5vw, 80px);
}

/* ─── Header ────────────────────────────────────── */
.services__header {
  max-width: 640px;
  margin-bottom: clamp(48px, 7vw, 80px);
}

.services__eyebrow {
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

.services__eyebrow-line {
  display: block;
  width: 32px;
  height: 1px;
  background: var(--coral);
  flex-shrink: 0;
}

.services__heading {
  display: flex;
  flex-direction: column;
  gap: 4px;
  font-family: var(--font-display);
  font-size: clamp(2.4rem, 4.5vw, 4rem);
  font-weight: 700;
  line-height: 1.1;
  letter-spacing: -0.02em;
  margin-bottom: 20px;
}

.services__heading-line {
  display: block;
  color: var(--white);
}

.services__heading-line--ghost {
  color: transparent;
  -webkit-text-stroke: 1.5px rgba(255,255,255,0.2);
}

.services__heading-sub {
  font-size: 0.93rem;
  line-height: 1.8;
  color: var(--grey-400);
  max-width: 520px;
}

/* ─── Grid ──────────────────────────────────────── */
.services__grid {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 1px;
  background: rgba(255,255,255,0.06);
  border: 1px solid rgba(255,255,255,0.06);
  border-radius: 12px;
  overflow: hidden;
  margin-bottom: 48px;
}

/* ─── Card ──────────────────────────────────────── */
.services__card {
  position: relative;
  background: var(--grey-900);
  padding: 36px 32px 32px;
  display: flex;
  flex-direction: column;
  gap: 14px;
  overflow: hidden;
  cursor: pointer;
  transition: background 0.35s var(--ease);
}

.services__card:hover {
  background: rgba(255,107,91,0.04);
}

.services__card--featured {
  background: rgba(255,107,91,0.05);
}

.services__card--featured::before {
  content: 'Most Popular';
  position: absolute;
  top: 20px;
  right: 20px;
  font-size: 0.58rem;
  font-weight: 600;
  letter-spacing: 0.18em;
  text-transform: uppercase;
  color: var(--coral);
  background: rgba(255,107,91,0.1);
  border: 1px solid rgba(255,107,91,0.2);
  padding: 4px 10px;
  border-radius: 20px;
}

/* Card number */
.services__card-num {
  font-family: var(--font-display);
  font-size: 0.7rem;
  font-weight: 400;
  letter-spacing: 0.2em;
  color: rgba(255,107,91,0.35);
}

/* Icon */
.services__icon-wrap {
  position: relative;
  width: 52px;
  height: 52px;
  display: flex;
  align-items: center;
  justify-content: center;
  margin-bottom: 4px;
}

.services__icon-bg {
  position: absolute;
  inset: 0;
  border-radius: 10px;
  background: rgba(255,107,91,0.08);
  border: 1px solid rgba(255,107,91,0.12);
  transition: background 0.3s var(--ease), border-color 0.3s;
}

.services__card:hover .services__icon-bg {
  background: rgba(255,107,91,0.14);
  border-color: rgba(255,107,91,0.25);
}

.services__icon {
  position: relative;
  z-index: 1;
  display: flex;
  align-items: center;
  justify-content: center;
  transition: transform 0.35s var(--ease-spring);
}

.services__card:hover .services__icon {
  transform: scale(1.1) rotate(-4deg);
}

/* Title */
.services__card-title {
  font-family: var(--font-display);
  font-size: 1.25rem;
  font-weight: 700;
  color: var(--white);
  line-height: 1.2;
  letter-spacing: -0.01em;
}

/* Desc */
.services__card-desc {
  font-size: 0.83rem;
  line-height: 1.75;
  color: var(--grey-400);
  flex: 1;
}

/* Tags */
.services__tags {
  display: flex;
  flex-wrap: wrap;
  gap: 6px;
  list-style: none;
}

.services__tag {
  font-size: 0.62rem;
  font-weight: 500;
  letter-spacing: 0.1em;
  text-transform: uppercase;
  color: rgba(255,255,255,0.4);
  border: 1px solid rgba(255,255,255,0.08);
  padding: 3px 10px;
  border-radius: 2px;
  transition: color 0.25s, border-color 0.25s;
}

.services__card:hover .services__tag {
  color: rgba(255,107,91,0.7);
  border-color: rgba(255,107,91,0.15);
}

/* Arrow */
.services__card-arrow {
  display: flex;
  align-items: center;
  color: var(--coral);
  opacity: 0;
  transform: translateX(-8px);
  transition: opacity 0.28s var(--ease), transform 0.28s var(--ease);
  margin-top: 4px;
}

.services__card:hover .services__card-arrow {
  opacity: 1;
  transform: translateX(0);
}

/* Glow on hover */
.services__card-glow {
  position: absolute;
  inset: 0;
  border-radius: inherit;
  opacity: 0;
  box-shadow: inset 0 0 0 1px rgba(255,107,91,0.2);
  transition: opacity 0.35s var(--ease);
  pointer-events: none;
}

.services__card:hover .services__card-glow {
  opacity: 1;
}

/* ─── CTA Strip ─────────────────────────────────── */
.services__cta-strip {
  display: flex;
  align-items: center;
  justify-content: space-between;
  gap: 32px;
  padding: 32px 40px;
  border: 1px solid rgba(255,255,255,0.07);
  border-radius: 10px;
  background: rgba(255,255,255,0.02);
  backdrop-filter: blur(10px);
}

.services__cta-strip-label {
  display: block;
  font-size: var(--text-xs);
  font-weight: 500;
  letter-spacing: 0.2em;
  text-transform: uppercase;
  color: var(--coral);
  margin-bottom: 6px;
}

.services__cta-strip-text {
  font-size: 0.88rem;
  color: rgba(255,255,255,0.5);
  line-height: 1.6;
}

.services__cta-btn {
  display: inline-flex;
  align-items: center;
  gap: 10px;
  padding: 14px 28px;
  background: var(--coral);
  color: var(--white);
  text-decoration: none;
  font-size: 0.78rem;
  font-weight: 500;
  letter-spacing: 0.1em;
  text-transform: uppercase;
  border-radius: var(--radius-sm);
  white-space: nowrap;
  flex-shrink: 0;
  box-shadow: 0 4px 24px rgba(255,107,91,0.28);
  transition: background 0.28s var(--ease), box-shadow 0.28s, transform 0.28s var(--ease);
}

.services__cta-btn:hover {
  background: var(--coral-dark);
  box-shadow: 0 8px 32px rgba(255,107,91,0.4);
  transform: translateY(-2px);
  color: var(--white);
}

.services__cta-btn svg {
  transition: transform 0.25s var(--ease);
}

.services__cta-btn:hover svg {
  transform: translateX(4px);
}

/* ─── Responsive ────────────────────────────────── */
@media (max-width: 1024px) {
  .services__grid {
    grid-template-columns: repeat(2, 1fr);
  }
}

@media (max-width: 680px) {
  .services__grid {
    grid-template-columns: 1fr;
  }

  .services__cta-strip {
    flex-direction: column;
    align-items: flex-start;
    padding: 28px 24px;
  }
}
</style>