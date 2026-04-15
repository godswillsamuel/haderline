<template>
  <section id="about" class="about">

    <!-- Background -->
    <div class="about__bg" aria-hidden="true">
      <div class="about__bg-glow"></div>
      <div class="about__bg-lines"></div>
    </div>

    <div class="about__container">

      <!-- ── LEFT — Sticky visual column ── -->
      <div class="about__left">

        <div class="about__visual">
          <!-- Main image frame -->
          <div class="about__img-frame">
            <div class="about__img-inner">
              <!-- Abstract financial visual built with CSS + SVG -->
              <svg class="about__svg" viewBox="0 0 380 460" fill="none" xmlns="http://www.w3.org/2000/svg">
                <!-- Background rect -->
                <rect width="380" height="460" fill="#161616"/>

                <!-- Grid lines -->
                <line x1="0" y1="92" x2="380" y2="92" stroke="rgba(255,255,255,0.04)" stroke-width="1"/>
                <line x1="0" y1="184" x2="380" y2="184" stroke="rgba(255,255,255,0.04)" stroke-width="1"/>
                <line x1="0" y1="276" x2="380" y2="276" stroke="rgba(255,255,255,0.04)" stroke-width="1"/>
                <line x1="0" y1="368" x2="380" y2="368" stroke="rgba(255,255,255,0.04)" stroke-width="1"/>
                <line x1="76" y1="0" x2="76" y2="460" stroke="rgba(255,255,255,0.04)" stroke-width="1"/>
                <line x1="152" y1="0" x2="152" y2="460" stroke="rgba(255,255,255,0.04)" stroke-width="1"/>
                <line x1="228" y1="0" x2="228" y2="460" stroke="rgba(255,255,255,0.04)" stroke-width="1"/>
                <line x1="304" y1="0" x2="304" y2="460" stroke="rgba(255,255,255,0.04)" stroke-width="1"/>

                <!-- Coral glow circle -->
                <circle cx="190" cy="230" r="140" fill="url(#aboutGrad)" />
                <defs>
                  <radialGradient id="aboutGrad" cx="50%" cy="50%" r="50%">
                    <stop offset="0%" stop-color="#FF6B5B" stop-opacity="0.1"/>
                    <stop offset="100%" stop-color="#FF6B5B" stop-opacity="0"/>
                  </radialGradient>
                </defs>

                <!-- Hexagon outline -->
                <polygon
                  class="about__hex"
                  points="190,60 310,130 310,270 190,340 70,270 70,130"
                  stroke="#FF6B5B" stroke-width="1" fill="none" opacity="0.18"
                />
                <polygon
                  class="about__hex about__hex--inner"
                  points="190,100 278,150 278,250 190,300 102,250 102,150"
                  stroke="#FF6B5B" stroke-width="0.8" fill="none" opacity="0.1"
                />

                <!-- Bar chart bars -->
                <rect class="about__bar" x="60" y="340" width="28" height="80" rx="2" fill="#FF6B5B" opacity="0.15"/>
                <rect class="about__bar" x="100" y="300" width="28" height="120" rx="2" fill="#FF6B5B" opacity="0.2"/>
                <rect class="about__bar" x="140" y="260" width="28" height="160" rx="2" fill="#FF6B5B" opacity="0.25"/>
                <rect class="about__bar" x="180" y="220" width="28" height="200" rx="2" fill="#FF6B5B" opacity="0.3"/>
                <rect class="about__bar about__bar--highlight" x="220" y="180" width="28" height="240" rx="2" fill="#FF6B5B" opacity="0.45"/>
                <rect class="about__bar" x="260" y="200" width="28" height="220" rx="2" fill="#FF6B5B" opacity="0.3"/>
                <rect class="about__bar" x="300" y="240" width="28" height="180" rx="2" fill="#FF6B5B" opacity="0.2"/>

                <!-- Trend line over bars -->
                <path
                  class="about__trend"
                  d="M74,340 L114,300 L154,258 L194,218 L234,178 L274,198 L314,238"
                  stroke="#FF6B5B" stroke-width="2" stroke-linecap="round" fill="none"
                />
                <circle cx="234" cy="178" r="5" fill="#FF6B5B"/>
                <circle cx="234" cy="178" r="9" stroke="#FF6B5B" stroke-width="1" fill="none" opacity="0.4"/>

                <!-- Top label -->
                <text x="190" y="44" text-anchor="middle" font-size="9" fill="rgba(255,255,255,0.25)" font-family="DM Sans, sans-serif" letter-spacing="3">ANNUAL RETURNS</text>

                <!-- Year labels -->
                <text x="74" y="440" text-anchor="middle" font-size="8" fill="rgba(255,255,255,0.2)" font-family="DM Sans, sans-serif">2018</text>
                <text x="114" y="440" text-anchor="middle" font-size="8" fill="rgba(255,255,255,0.2)" font-family="DM Sans, sans-serif">2019</text>
                <text x="154" y="440" text-anchor="middle" font-size="8" fill="rgba(255,255,255,0.2)" font-family="DM Sans, sans-serif">2020</text>
                <text x="194" y="440" text-anchor="middle" font-size="8" fill="rgba(255,255,255,0.2)" font-family="DM Sans, sans-serif">2021</text>
                <text x="234" y="440" text-anchor="middle" font-size="8" fill="rgba(255,255,255,0.2)" font-family="DM Sans, sans-serif">2022</text>
                <text x="274" y="440" text-anchor="middle" font-size="8" fill="rgba(255,255,255,0.2)" font-family="DM Sans, sans-serif">2023</text>
                <text x="314" y="440" text-anchor="middle" font-size="8" fill="rgba(255,255,255,0.2)" font-family="DM Sans, sans-serif">2024</text>
              </svg>
            </div>

            <!-- Floating badge -->
            <div class="about__badge">
              <span class="about__badge-icon">◈</span>
              <div>
                <div class="about__badge-val">19+ Years</div>
                <div class="about__badge-label">Market Excellence</div>
              </div>
            </div>

            <!-- Corner accent lines -->
            <span class="about__corner about__corner--tl"></span>
            <span class="about__corner about__corner--br"></span>
          </div>

          <!-- Small trust card -->
          <div class="about__trust-card">
            <div class="about__trust-avatars">
              <span v-for="n in 4" :key="n" class="about__avatar" :style="`--n: ${n}`">
                {{ ['A','R','S','M'][n-1] }}
              </span>
            </div>
            <div class="about__trust-text">
              <strong>2,400+ clients</strong> trust Harderlin with their financial future
            </div>
          </div>
        </div>

      </div>

      <!-- ── RIGHT — Content column ── -->
      <div class="about__right">

        <div class="about__eyebrow">
          <span class="about__eyebrow-line"></span>
          <span>Who We Are</span>
        </div>

        <h2 class="about__heading">
          <span class="about__heading-line">Two Decades of</span>
          <span class="about__heading-line about__heading-line--ghost">Disciplined</span>
          <span class="about__heading-line about__heading-line--coral">Investing.</span>
        </h2>

        <p class="about__lead">
          Founded in 2004, Harderlin Investment Group was built on a single conviction —
          that intelligent, patient capital allocation creates enduring wealth.
        </p>

        <p class="about__body">
          We combine deep macroeconomic research with rigorous portfolio construction to
          navigate every market environment. Our team of 60+ investment professionals
          manages capital across asset classes, geographies, and risk profiles — always
          with the long-term in mind.
        </p>

        <!-- Pillars -->
        <div class="about__pillars">
          <div v-for="(pillar, i) in pillars" :key="pillar.title" class="about__pillar" :style="`--pi: ${i}`">
            <span class="about__pillar-num">0{{ i + 1 }}</span>
            <div class="about__pillar-content">
              <h4 class="about__pillar-title">{{ pillar.title }}</h4>
              <p class="about__pillar-desc">{{ pillar.desc }}</p>
            </div>
          </div>
        </div>

        <!-- Team strip -->
        <div class="about__team-strip">
          <div class="about__team-strip-label">
            <span class="about__eyebrow-line"></span>
            <span>Leadership</span>
          </div>
          <div class="about__team-members">
            <div v-for="member in team" :key="member.name" class="about__member">
              <div class="about__member-avatar">{{ member.initials }}</div>
              <div>
                <div class="about__member-name">{{ member.name }}</div>
                <div class="about__member-role">{{ member.role }}</div>
              </div>
            </div>
          </div>
        </div>

        <a href="#services" class="about__cta">
          <span>Explore Our Approach</span>
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
  name: 'AboutSection',
  data() {
    return {
      pillars: [
        {
          title: 'Research-Driven',
          desc: 'Every decision is grounded in rigorous macroeconomic analysis and proprietary data modelling.',
        },
        {
          title: 'Risk Disciplined',
          desc: 'Downside protection is as important as upside capture. We never chase returns at the expense of capital.',
        },
        {
          title: 'Client-Aligned',
          desc: 'Our fee structure ensures our interests are fully aligned with yours — we grow when you grow.',
        },
      ],
      team: [
        { name: 'James Harderlin', role: 'Founder & CIO',       initials: 'JH' },
        { name: 'Amara Osei',      role: 'Managing Director',    initials: 'AO' },
        { name: 'Rachel Stern',    role: 'Head of Fixed Income', initials: 'RS' },
      ],
    };
  },
};
</script>

<style scoped>

/* ─── Section ───────────────────────────────────── */
.about {
  position: relative;
  padding-block: var(--section-pad);
  background: var(--grey-950);
  overflow: hidden;
}

/* ─── Background ────────────────────────────────── */
.about__bg { position: absolute; inset: 0; pointer-events: none; }

.about__bg-glow {
  position: absolute;
  right: -10%;
  bottom: 0;
  width: 500px;
  height: 500px;
  background: radial-gradient(circle, rgba(255,107,91,0.07) 0%, transparent 65%);
  border-radius: 50%;
}

.about__bg-lines {
  position: absolute;
  inset: 0;
  background-image:
    linear-gradient(rgba(255,255,255,0.025) 1px, transparent 1px),
    linear-gradient(90deg, rgba(255,255,255,0.025) 1px, transparent 1px);
  background-size: 80px 80px;
  mask-image: radial-gradient(ellipse 70% 70% at 80% 50%, black, transparent);
}

/* ─── Container ─────────────────────────────────── */
.about__container {
  position: relative;
  z-index: 1;
  max-width: var(--max-width);
  margin: 0 auto;
  padding-inline: clamp(24px, 5vw, 80px);
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: clamp(48px, 7vw, 100px);
  align-items: center;
}

/* ─── LEFT ──────────────────────────────────────── */
.about__left {
  position: relative;
}

.about__visual {
  position: relative;
}

/* Image frame */
.about__img-frame {
  position: relative;
  border-radius: 12px;
  overflow: visible;
}

.about__img-inner {
  border-radius: 12px;
  overflow: hidden;
  border: 1px solid rgba(255,255,255,0.07);
  box-shadow: 0 32px 80px rgba(0,0,0,0.5);
}

.about__svg {
  display: block;
  width: 100%;
  height: auto;
}

/* SVG animations */
.about__hex {
  stroke-dasharray: 800;
  stroke-dashoffset: 800;
  animation: hexDraw 2s 0.4s var(--ease) forwards;
}
.about__hex--inner {
  animation-delay: 0.8s;
}

@keyframes hexDraw { to { stroke-dashoffset: 0; } }

.about__bar {
  transform-origin: bottom center;
  animation: barRise 0.8s var(--ease-spring) both;
}
.about__bar:nth-child(1)  { animation-delay: 0.5s; }
.about__bar:nth-child(2)  { animation-delay: 0.6s; }
.about__bar:nth-child(3)  { animation-delay: 0.7s; }
.about__bar:nth-child(4)  { animation-delay: 0.8s; }
.about__bar:nth-child(5)  { animation-delay: 0.9s; }
.about__bar:nth-child(6)  { animation-delay: 1.0s; }
.about__bar:nth-child(7)  { animation-delay: 1.1s; }

@keyframes barRise {
  from { transform: scaleY(0); opacity: 0; }
  to   { transform: scaleY(1); opacity: 1; }
}

.about__trend {
  stroke-dasharray: 400;
  stroke-dashoffset: 400;
  animation: trendDraw 1.2s 1.2s var(--ease) forwards;
}
@keyframes trendDraw { to { stroke-dashoffset: 0; } }

/* Corner accents */
.about__corner {
  position: absolute;
  width: 20px;
  height: 20px;
  pointer-events: none;
}
.about__corner--tl {
  top: -6px; left: -6px;
  border-top: 2px solid var(--coral);
  border-left: 2px solid var(--coral);
}
.about__corner--br {
  bottom: -6px; right: -6px;
  border-bottom: 2px solid var(--coral);
  border-right: 2px solid var(--coral);
}

/* Floating badge */
.about__badge {
  position: absolute;
  top: 24px;
  right: -24px;
  display: flex;
  align-items: center;
  gap: 12px;
  padding: 14px 18px;
  background: rgba(20,20,20,0.92);
  border: 1px solid rgba(255,255,255,0.08);
  border-radius: 10px;
  backdrop-filter: blur(20px);
  box-shadow: 0 16px 40px rgba(0,0,0,0.4);
  animation: cardIn 0.8s 1.4s var(--ease-spring) both;
  white-space: nowrap;
}

@keyframes cardIn {
  from { opacity: 0; transform: translateY(16px) scale(0.95); }
  to   { opacity: 1; transform: translateY(0) scale(1); }
}

.about__badge-icon {
  font-size: 1.3rem;
  color: var(--coral);
}
.about__badge-val {
  font-family: var(--font-display);
  font-size: 1.1rem;
  font-weight: 700;
  color: var(--white);
  line-height: 1;
}
.about__badge-label {
  font-size: 0.6rem;
  letter-spacing: 0.15em;
  text-transform: uppercase;
  color: var(--grey-400);
  margin-top: 2px;
}

/* Trust card */
.about__trust-card {
  display: flex;
  align-items: center;
  gap: 14px;
  margin-top: 20px;
  padding: 16px 20px;
  background: rgba(255,255,255,0.03);
  border: 1px solid rgba(255,255,255,0.06);
  border-radius: 8px;
  animation: cardIn 0.8s 1.6s var(--ease-spring) both;
}

.about__trust-avatars {
  display: flex;
  align-items: center;
}

.about__avatar {
  width: 32px;
  height: 32px;
  border-radius: 50%;
  background: linear-gradient(135deg, var(--grey-700), var(--grey-800));
  border: 2px solid var(--grey-950);
  display: flex;
  align-items: center;
  justify-content: center;
  font-size: 0.65rem;
  font-weight: 600;
  color: var(--coral);
  margin-left: calc(var(--n) * -8px + 8px);
  flex-shrink: 0;
}

.about__trust-text {
  font-size: 0.75rem;
  color: var(--grey-400);
  line-height: 1.5;
}

.about__trust-text strong {
  color: var(--white);
  font-weight: 600;
}

/* ─── RIGHT ─────────────────────────────────────── */
.about__right {
  display: flex;
  flex-direction: column;
  gap: 0;
}

.about__eyebrow {
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

.about__eyebrow-line {
  display: block;
  width: 32px;
  height: 1px;
  background: var(--coral);
  flex-shrink: 0;
}

/* Heading */
.about__heading {
  display: flex;
  flex-direction: column;
  gap: 2px;
  font-family: var(--font-display);
  font-size: clamp(2.2rem, 4vw, 3.6rem);
  font-weight: 700;
  line-height: 1.1;
  letter-spacing: -0.02em;
  margin-bottom: 24px;
}

.about__heading-line       { color: var(--white); }
.about__heading-line--ghost {
  color: transparent;
  -webkit-text-stroke: 1.5px rgba(255,255,255,0.2);
}
.about__heading-line--coral { color: var(--coral); }

/* Copy */
.about__lead {
  font-size: 1rem;
  line-height: 1.8;
  color: rgba(255,255,255,0.7);
  margin-bottom: 16px;
}

.about__body {
  font-size: 0.88rem;
  line-height: 1.85;
  color: var(--grey-400);
  margin-bottom: 40px;
}

/* Pillars */
.about__pillars {
  display: flex;
  flex-direction: column;
  gap: 0;
  margin-bottom: 40px;
  border-top: 1px solid rgba(255,255,255,0.06);
}

.about__pillar {
  display: flex;
  gap: 20px;
  padding: 20px 0;
  border-bottom: 1px solid rgba(255,255,255,0.06);
  transition: background 0.25s;
  cursor: default;
}

.about__pillar:hover .about__pillar-title {
  color: var(--coral);
}

.about__pillar-num {
  font-family: var(--font-display);
  font-size: 0.68rem;
  letter-spacing: 0.18em;
  color: rgba(255,107,91,0.4);
  padding-top: 3px;
  flex-shrink: 0;
  width: 28px;
}

.about__pillar-title {
  font-family: var(--font-display);
  font-size: 1.05rem;
  font-weight: 700;
  color: var(--white);
  margin-bottom: 4px;
  transition: color 0.25s var(--ease);
}

.about__pillar-desc {
  font-size: 0.82rem;
  line-height: 1.7;
  color: var(--grey-400);
}

/* Team strip */
.about__team-strip {
  margin-bottom: 36px;
}

.about__team-strip-label {
  display: flex;
  align-items: center;
  gap: 10px;
  font-size: var(--text-xs);
  font-weight: 500;
  letter-spacing: 0.2em;
  text-transform: uppercase;
  color: rgba(255,255,255,0.3);
  margin-bottom: 16px;
}

.about__team-members {
  display: flex;
  gap: 16px;
  flex-wrap: wrap;
}

.about__member {
  display: flex;
  align-items: center;
  gap: 12px;
  padding: 12px 16px;
  background: rgba(255,255,255,0.03);
  border: 1px solid rgba(255,255,255,0.06);
  border-radius: 8px;
  flex: 1;
  min-width: 160px;
  transition: border-color 0.25s, background 0.25s;
}

.about__member:hover {
  border-color: rgba(255,107,91,0.2);
  background: rgba(255,107,91,0.04);
}

.about__member-avatar {
  width: 36px;
  height: 36px;
  border-radius: 50%;
  background: rgba(255,107,91,0.1);
  border: 1px solid rgba(255,107,91,0.2);
  display: flex;
  align-items: center;
  justify-content: center;
  font-size: 0.68rem;
  font-weight: 700;
  color: var(--coral);
  flex-shrink: 0;
  letter-spacing: 0.05em;
}

.about__member-name {
  font-size: 0.78rem;
  font-weight: 600;
  color: var(--white);
  line-height: 1.3;
}

.about__member-role {
  font-size: 0.65rem;
  letter-spacing: 0.08em;
  color: var(--grey-400);
  margin-top: 1px;
}

/* CTA */
.about__cta {
  display: inline-flex;
  align-items: center;
  gap: 10px;
  padding: 13px 26px;
  color: var(--white);
  text-decoration: none;
  font-size: 0.78rem;
  font-weight: 500;
  letter-spacing: 0.1em;
  text-transform: uppercase;
  border: 1px solid rgba(255,107,91,0.4);
  border-radius: var(--radius-sm);
  align-self: flex-start;
  transition: border-color 0.28s, box-shadow 0.28s, color 0.28s, transform 0.28s var(--ease);
}

.about__cta:hover {
  border-color: var(--coral);
  box-shadow: 0 0 0 1px var(--coral), inset 0 0 20px rgba(255,107,91,0.05);
  color: var(--white);
  transform: translateY(-2px);
}

.about__cta svg {
  transition: transform 0.25s var(--ease);
}
.about__cta:hover svg {
  transform: translateX(4px);
}

/* ─── Responsive ────────────────────────────────── */
@media (max-width: 1024px) {
  .about__container {
    grid-template-columns: 1fr;
  }

  .about__left {
    max-width: 500px;
    margin: 0 auto;
  }

  .about__badge {
    right: 0;
  }
}

@media (max-width: 600px) {
  .about__team-members {
    flex-direction: column;
  }

  .about__badge {
    position: relative;
    top: auto; right: auto;
    margin-top: 16px;
    width: fit-content;
  }
}
</style>