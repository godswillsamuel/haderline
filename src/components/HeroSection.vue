<template>
  <section id="home" class="hero">

    <!-- Background layers -->
    <div class="hero__bg">
      <div class="hero__bg-grid"></div>
      <div class="hero__bg-glow"></div>
      <div class="hero__bg-noise"></div>
    </div>

    <!-- Floating ticker tape -->
    <div class="hero__ticker" aria-hidden="true">
      <div class="hero__ticker-track">
        <span v-for="(item, i) in [...tickers, ...tickers]" :key="i" class="hero__ticker-item">
          <span class="hero__ticker-symbol">{{ item.symbol }}</span>
          <span :class="['hero__ticker-val', item.up ? 'up' : 'down']">
            {{ item.up ? '▲' : '▼' }} {{ item.val }}
          </span>
        </span>
      </div>
    </div>

    <!-- Main content -->
    <div class="hero__container">

      <!-- Left column -->
      <div class="hero__left">

        <div class="hero__eyebrow">
          <span class="hero__eyebrow-line"></span>
          <span class="hero__eyebrow-text">Trusted Since 2004</span>
        </div>

        <h1 class="hero__heading">
          <span class="hero__heading-row">
            <span class="hero__word" style="--wd: 0">Invest</span>
          </span>
          <span class="hero__heading-row hero__heading-row--indent">
            <span class="hero__word hero__word--outline" style="--wd: 1">With</span>
            <span class="hero__word hero__word--coral" style="--wd: 2">Purpose.</span>
          </span>
          <span class="hero__heading-row">
            <span class="hero__word" style="--wd: 3">Grow</span>
            <span class="hero__word hero__word--outline" style="--wd: 4">With</span>
          </span>
          <span class="hero__heading-row hero__heading-row--indent2">
            <span class="hero__word hero__word--coral" style="--wd: 5">Confidence.</span>
          </span>
        </h1>

        <p class="hero__sub" style="--wd: 6">
          Harderlin partners with individuals and institutions to build
          resilient, long-term wealth through disciplined strategy and
          market expertise.
        </p>

        <div class="hero__actions" style="--wd: 7">
          <a href="#services" class="hero__btn hero__btn--primary">
            <span>Explore Our Funds</span>
            <svg width="16" height="16" viewBox="0 0 16 16" fill="none">
              <path d="M3 8h10M9 4l4 4-4 4" stroke="currentColor" stroke-width="1.4" stroke-linecap="round" stroke-linejoin="round"/>
            </svg>
          </a>
          <a href="#about" class="hero__btn hero__btn--ghost">
            <span class="hero__btn-play">
              <svg width="10" height="12" viewBox="0 0 10 12" fill="none">
                <path d="M1 1l8 5-8 5V1z" fill="currentColor"/>
              </svg>
            </span>
            <span>Watch Overview</span>
          </a>
        </div>

        <!-- Stat strip -->
        <div class="hero__stats" style="--wd: 8">
          <div v-for="(stat, i) in stats" :key="i" class="hero__stat">
            <span class="hero__stat-value">{{ stat.value }}</span>
            <span class="hero__stat-label">{{ stat.label }}</span>
          </div>
          <div class="hero__stat-divider"></div>
        </div>

      </div>

      <!-- Right column — abstract chart visual -->
      <div class="hero__right" aria-hidden="true">

        <div class="hero__visual">
          <!-- Floating card -->
          <div class="hero__card hero__card--main">
            <div class="hero__card-header">
              <span class="hero__card-dot"></span>
              <span class="hero__card-title">Portfolio Growth</span>
              <span class="hero__card-badge">+24.6%</span>
            </div>
            <div class="hero__chart">
              <svg viewBox="0 0 260 100" preserveAspectRatio="none" class="hero__chart-svg">
                <defs>
                  <linearGradient id="chartGrad" x1="0" y1="0" x2="0" y2="1">
                    <stop offset="0%" stop-color="#FF6B5B" stop-opacity="0.35"/>
                    <stop offset="100%" stop-color="#FF6B5B" stop-opacity="0"/>
                  </linearGradient>
                </defs>
                <path
                  class="hero__chart-area"
                  d="M0,80 C20,75 40,70 60,58 C80,46 90,50 110,40 C130,30 140,35 160,22 C180,10 200,15 220,8 C235,4 248,6 260,3 L260,100 L0,100 Z"
                  fill="url(#chartGrad)"
                />
                <path
                  class="hero__chart-line"
                  d="M0,80 C20,75 40,70 60,58 C80,46 90,50 110,40 C130,30 140,35 160,22 C180,10 200,15 220,8 C235,4 248,6 260,3"
                  fill="none"
                  stroke="#FF6B5B"
                  stroke-width="2"
                  stroke-linecap="round"
                />
                <!-- Animated dot at end of line -->
                <circle class="hero__chart-dot" cx="260" cy="3" r="4" fill="#FF6B5B"/>
                <circle class="hero__chart-dot-ring" cx="260" cy="3" r="4" fill="none" stroke="#FF6B5B" stroke-width="1.5"/>
              </svg>
            </div>
            <div class="hero__chart-labels">
              <span>Jan</span><span>Mar</span><span>Jun</span><span>Sep</span><span>Dec</span>
            </div>
          </div>

          <!-- Mini floating cards -->
          <div class="hero__card hero__card--mini hero__card--top">
            <span class="hero__mini-icon">◈</span>
            <div>
              <div class="hero__mini-val">$4.2B</div>
              <div class="hero__mini-label">Assets Under Management</div>
            </div>
          </div>

          <div class="hero__card hero__card--mini hero__card--bot">
            <span class="hero__mini-icon hero__mini-icon--green">⬡</span>
            <div>
              <div class="hero__mini-val">98.3%</div>
              <div class="hero__mini-label">Client Retention Rate</div>
            </div>
          </div>

          <!-- Decorative rings -->
          <div class="hero__ring hero__ring--1"></div>
          <div class="hero__ring hero__ring--2"></div>
        </div>

      </div>

    </div>

    <!-- Scroll cue -->
    <div class="hero__scroll-cue">
      <span class="hero__scroll-line"></span>
      <span class="hero__scroll-label">Scroll</span>
    </div>

  </section>
</template>

<script>
export default {
  name: 'HeroSection',
  data() {
    return {
      stats: [
        { value: '$4.2B+', label: 'Assets Managed' },
        { value: '2,400+', label: 'Clients Worldwide' },
        { value: '19yr',   label: 'Market Experience' },
      ],
      tickers: [
        { symbol: 'AAPL',  val: '189.42', up: true  },
        { symbol: 'MSFT',  val: '374.10', up: true  },
        { symbol: 'TSLA',  val: '242.80', up: false },
        { symbol: 'GOOGL', val: '140.55', up: true  },
        { symbol: 'AMZN',  val: '178.22', up: true  },
        { symbol: 'BRK.B', val: '366.90', up: false },
        { symbol: 'JPM',   val: '196.45', up: true  },
        { symbol: 'GS',    val: '449.30', up: false },
        { symbol: 'BLK',   val: '812.60', up: true  },
        { symbol: 'V',     val: '271.15', up: true  },
      ],
    };
  },
};
</script>

<style scoped>

/* ─── Section Shell ─────────────────────────────── */
.hero {
  position: relative;
  min-height: 100vh;
  display: flex;
  flex-direction: column;
  overflow: hidden;
  background: var(--grey-950);
  padding-top: var(--nav-height);
}

/* ─── Background ────────────────────────────────── */
.hero__bg {
  position: absolute;
  inset: 0;
  pointer-events: none;
  z-index: 0;
}

/* Subtle dot grid */
.hero__bg-grid {
  position: absolute;
  inset: 0;
  background-image: radial-gradient(rgba(255,255,255,0.045) 1px, transparent 1px);
  background-size: 36px 36px;
}

/* Coral glow blob bottom-right */
.hero__bg-glow {
  position: absolute;
  right: -10%;
  top: 10%;
  width: 700px;
  height: 700px;
  background: radial-gradient(circle, rgba(255,107,91,0.09) 0%, transparent 65%);
  border-radius: 50%;
  animation: glow-drift 10s ease-in-out infinite alternate;
}

@keyframes glow-drift {
  from { transform: translate(0, 0) scale(1); }
  to   { transform: translate(-40px, 40px) scale(1.08); }
}

/* Grain overlay */
.hero__bg-noise {
  position: absolute;
  inset: 0;
  opacity: 0.025;
  background-image: url("data:image/svg+xml,%3Csvg viewBox='0 0 256 256' xmlns='http://www.w3.org/2000/svg'%3E%3Cfilter id='noise'%3E%3CfeTurbulence type='fractalNoise' baseFrequency='0.9' numOctaves='4' stitchTiles='stitch'/%3E%3C/filter%3E%3Crect width='100%25' height='100%25' filter='url(%23noise)'/%3E%3C/svg%3E");
  background-size: 200px 200px;
}

/* ─── Ticker ────────────────────────────────────── */
.hero__ticker {
  position: relative;
  z-index: 2;
  border-top: 1px solid rgba(255,255,255,0.05);
  border-bottom: 1px solid rgba(255,255,255,0.05);
  background: rgba(255,255,255,0.02);
  overflow: hidden;
  height: 36px;
  display: flex;
  align-items: center;
}

.hero__ticker-track {
  display: flex;
  gap: 0;
  white-space: nowrap;
  animation: ticker 35s linear infinite;
  will-change: transform;
}

@keyframes ticker {
  from { transform: translateX(0); }
  to   { transform: translateX(-50%); }
}

.hero__ticker-item {
  display: inline-flex;
  align-items: center;
  gap: 6px;
  padding: 0 28px;
  font-size: 0.68rem;
  letter-spacing: 0.08em;
  border-right: 1px solid rgba(255,255,255,0.06);
}

.hero__ticker-symbol {
  color: rgba(255,255,255,0.5);
  font-weight: 500;
}

.hero__ticker-val {
  font-weight: 400;
}

.hero__ticker-val.up   { color: #4ade80; }
.hero__ticker-val.down { color: #f87171; }

/* ─── Container ─────────────────────────────────── */
.hero__container {
  position: relative;
  z-index: 2;
  flex: 1;
  display: grid;
  grid-template-columns: 1fr 1fr;
  align-items: center;
  gap: 60px;
  max-width: var(--max-width);
  margin: 0 auto;
  padding: clamp(48px, 8vh, 100px) clamp(24px, 5vw, 80px);
  width: 100%;
}

/* ─── Eyebrow ───────────────────────────────────── */
.hero__eyebrow {
  display: flex;
  align-items: center;
  gap: 12px;
  margin-bottom: 28px;
  animation: fadeUp 0.7s 0.2s var(--ease) both;
}

.hero__eyebrow-line {
  display: block;
  width: 32px;
  height: 1px;
  background: var(--coral);
}

.hero__eyebrow-text {
  font-size: var(--text-xs);
  font-weight: 500;
  letter-spacing: 0.22em;
  text-transform: uppercase;
  color: var(--coral);
}

/* ─── Heading ───────────────────────────────────── */
.hero__heading {
  display: flex;
  flex-direction: column;
  gap: 2px;
  font-family: var(--font-display);
  font-size: clamp(3.4rem, 6vw, 6rem);
  font-weight: 700;
  line-height: 1.0;
  letter-spacing: -0.02em;
  margin-bottom: 28px;
}

.hero__heading-row {
  display: flex;
  align-items: baseline;
  gap: 18px;
  overflow: hidden;
}

.hero__heading-row--indent  { padding-left: 48px; }
.hero__heading-row--indent2 { padding-left: 96px; }

.hero__word {
  display: inline-block;
  color: var(--white);
  animation: wordReveal 0.75s calc(0.3s + var(--wd) * 0.09s) var(--ease-spring) both;
}

.hero__word--outline {
  color: transparent;
  -webkit-text-stroke: 1.5px rgba(255,255,255,0.3);
}

.hero__word--coral {
  color: var(--coral);
}

@keyframes wordReveal {
  from { opacity: 0; transform: translateY(40px) skewY(3deg); }
  to   { opacity: 1; transform: translateY(0) skewY(0); }
}

/* ─── Subheading ────────────────────────────────── */
.hero__sub {
  max-width: 420px;
  font-size: 0.95rem;
  line-height: 1.8;
  color: var(--grey-400);
  margin-bottom: 40px;
  animation: fadeUp 0.7s calc(0.3s + 6 * 0.09s) var(--ease) both;
}

/* ─── Action Buttons ────────────────────────────── */
.hero__actions {
  display: flex;
  align-items: center;
  gap: 16px;
  margin-bottom: 56px;
  animation: fadeUp 0.7s calc(0.3s + 7 * 0.09s) var(--ease) both;
}

.hero__btn {
  display: inline-flex;
  align-items: center;
  gap: 10px;
  text-decoration: none;
  font-size: 0.78rem;
  font-weight: 500;
  letter-spacing: 0.1em;
  text-transform: uppercase;
  border-radius: var(--radius-sm);
  transition: all 0.28s var(--ease);
}

.hero__btn--primary {
  padding: 14px 28px;
  background: var(--coral);
  color: var(--white);
  box-shadow: 0 4px 24px rgba(255,107,91,0.3);
}

.hero__btn--primary:hover {
  background: var(--coral-dark);
  box-shadow: 0 8px 32px rgba(255,107,91,0.45);
  transform: translateY(-2px);
  color: var(--white);
}

.hero__btn--primary svg {
  transition: transform 0.25s var(--ease);
}

.hero__btn--primary:hover svg {
  transform: translateX(4px);
}

.hero__btn--ghost {
  padding: 13px 24px;
  color: rgba(255,255,255,0.6);
  border: 1px solid rgba(255,255,255,0.12);
  gap: 12px;
}

.hero__btn--ghost:hover {
  color: var(--white);
  border-color: rgba(255,255,255,0.3);
  transform: translateY(-2px);
}

.hero__btn-play {
  display: flex;
  align-items: center;
  justify-content: center;
  width: 28px;
  height: 28px;
  border-radius: 50%;
  border: 1px solid rgba(255,255,255,0.2);
  flex-shrink: 0;
  transition: border-color 0.25s, background 0.25s;
}

.hero__btn--ghost:hover .hero__btn-play {
  border-color: var(--coral);
  background: var(--coral-soft);
}

/* ─── Stats ─────────────────────────────────────── */
.hero__stats {
  display: flex;
  align-items: flex-start;
  gap: 36px;
  position: relative;
  animation: fadeUp 0.7s calc(0.3s + 8 * 0.09s) var(--ease) both;
}

.hero__stat {
  display: flex;
  flex-direction: column;
  gap: 4px;
}

.hero__stat-value {
  font-family: var(--font-display);
  font-size: 1.8rem;
  font-weight: 700;
  color: var(--white);
  line-height: 1;
  letter-spacing: -0.02em;
}

.hero__stat-label {
  font-size: 0.68rem;
  letter-spacing: 0.14em;
  text-transform: uppercase;
  color: var(--grey-400);
}

.hero__stat-divider {
  position: absolute;
  bottom: -20px;
  left: 0;
  right: 0;
  height: 1px;
  background: linear-gradient(90deg, rgba(255,107,91,0.3), transparent);
}

/* ─── Right Visual ──────────────────────────────── */
.hero__right {
  display: flex;
  align-items: center;
  justify-content: center;
  animation: fadeIn 1s 0.6s var(--ease) both;
}

.hero__visual {
  position: relative;
  width: 100%;
  max-width: 480px;
  aspect-ratio: 1 / 0.9;
}

/* Main chart card */
.hero__card {
  background: rgba(255,255,255,0.035);
  border: 1px solid rgba(255,255,255,0.08);
  border-radius: 12px;
  backdrop-filter: blur(20px);
  -webkit-backdrop-filter: blur(20px);
  box-shadow: 0 24px 64px rgba(0,0,0,0.4),
              inset 0 1px 0 rgba(255,255,255,0.07);
}

.hero__card--main {
  position: absolute;
  inset: 0;
  padding: 24px;
  display: flex;
  flex-direction: column;
  gap: 16px;
  animation: cardIn 0.9s 0.8s var(--ease-spring) both;
}

@keyframes cardIn {
  from { opacity: 0; transform: translateY(30px) scale(0.96); }
  to   { opacity: 1; transform: translateY(0) scale(1); }
}

.hero__card-header {
  display: flex;
  align-items: center;
  gap: 8px;
}

.hero__card-dot {
  width: 8px;
  height: 8px;
  border-radius: 50%;
  background: var(--coral);
  animation: pulseGlow 2s ease-in-out infinite;
}

.hero__card-title {
  font-size: 0.75rem;
  font-weight: 500;
  letter-spacing: 0.1em;
  text-transform: uppercase;
  color: rgba(255,255,255,0.5);
  flex: 1;
}

.hero__card-badge {
  font-size: 0.72rem;
  font-weight: 600;
  color: #4ade80;
  background: rgba(74,222,128,0.1);
  border: 1px solid rgba(74,222,128,0.2);
  padding: 3px 10px;
  border-radius: 20px;
  letter-spacing: 0.05em;
}

/* Chart SVG */
.hero__chart {
  flex: 1;
  overflow: hidden;
}

.hero__chart-svg {
  width: 100%;
  height: 100%;
}

.hero__chart-area {
  animation: chartFill 1.5s 1s var(--ease) both;
}

.hero__chart-line {
  stroke-dasharray: 600;
  stroke-dashoffset: 600;
  animation: chartDraw 1.5s 1s var(--ease) forwards;
}

@keyframes chartDraw {
  to { stroke-dashoffset: 0; }
}

@keyframes chartFill {
  from { opacity: 0; }
  to   { opacity: 1; }
}

.hero__chart-dot {
  animation: chartDraw 1.5s 1s var(--ease) forwards, pulseDot 2s 2.5s ease-in-out infinite;
}

.hero__chart-dot-ring {
  animation: chartDraw 1.5s 1s var(--ease) forwards, ringPulse 2s 2.5s ease-in-out infinite;
}

@keyframes pulseDot {
  0%, 100% { r: 4; opacity: 1; }
  50%       { r: 5; opacity: 0.8; }
}

@keyframes ringPulse {
  0%, 100% { r: 4; opacity: 0.6; }
  50%       { r: 10; opacity: 0; }
}

.hero__chart-labels {
  display: flex;
  justify-content: space-between;
  font-size: 0.62rem;
  color: rgba(255,255,255,0.25);
  letter-spacing: 0.08em;
  padding: 0 2px;
}

/* Mini floating cards */
.hero__card--mini {
  position: absolute;
  display: flex;
  align-items: center;
  gap: 12px;
  padding: 14px 18px;
  min-width: 200px;
  z-index: 2;
}

.hero__card--top {
  top: -20px;
  right: -24px;
  animation: cardIn 0.8s 1.3s var(--ease-spring) both;
}

.hero__card--bot {
  bottom: -20px;
  left: -24px;
  animation: cardIn 0.8s 1.5s var(--ease-spring) both;
}

.hero__mini-icon {
  font-size: 1.2rem;
  color: var(--coral);
  flex-shrink: 0;
}

.hero__mini-icon--green {
  color: #4ade80;
}

.hero__mini-val {
  font-family: var(--font-display);
  font-size: 1.2rem;
  font-weight: 700;
  color: var(--white);
  line-height: 1;
}

.hero__mini-label {
  font-size: 0.62rem;
  letter-spacing: 0.1em;
  text-transform: uppercase;
  color: rgba(255,255,255,0.4);
  margin-top: 2px;
}

/* Decorative rings */
.hero__ring {
  position: absolute;
  border-radius: 50%;
  border: 1px solid rgba(255,107,91,0.08);
  pointer-events: none;
  animation: ringRotate 20s linear infinite;
}

.hero__ring--1 {
  width: 110%;
  aspect-ratio: 1;
  top: 50%; left: 50%;
  transform: translate(-50%, -50%);
}

.hero__ring--2 {
  width: 130%;
  aspect-ratio: 1;
  top: 50%; left: 50%;
  transform: translate(-50%, -50%);
  animation-duration: 30s;
  animation-direction: reverse;
  border-style: dashed;
  opacity: 0.5;
}

@keyframes ringRotate {
  to { transform: translate(-50%, -50%) rotate(360deg); }
}

/* ─── Scroll Cue ────────────────────────────────── */
.hero__scroll-cue {
  position: relative;
  z-index: 2;
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 8px;
  padding-bottom: 32px;
  animation: fadeIn 1s 1.8s var(--ease) both;
}

.hero__scroll-line {
  display: block;
  width: 1px;
  height: 48px;
  background: linear-gradient(to bottom, transparent, var(--coral));
  animation: scrollPulse 2s ease-in-out infinite;
}

@keyframes scrollPulse {
  0%, 100% { transform: scaleY(1); opacity: 1; }
  50%       { transform: scaleY(0.6); opacity: 0.4; }
}

.hero__scroll-label {
  font-size: 0.6rem;
  letter-spacing: 0.25em;
  text-transform: uppercase;
  color: rgba(255,255,255,0.3);
}

/* ─── Responsive ────────────────────────────────── */
@media (max-width: 1024px) {
  .hero__container {
    grid-template-columns: 1fr;
    gap: 48px;
  }

  .hero__right {
    display: none;
  }

  .hero__heading {
    font-size: clamp(3rem, 10vw, 5rem);
  }

  .hero__heading-row--indent  { padding-left: 32px; }
  .hero__heading-row--indent2 { padding-left: 64px; }
}

@media (max-width: 600px) {
  .hero__stats {
    gap: 24px;
  }

  .hero__actions {
    flex-direction: column;
    align-items: flex-start;
  }

  .hero__heading-row--indent  { padding-left: 20px; }
  .hero__heading-row--indent2 { padding-left: 40px; }
}
</style>