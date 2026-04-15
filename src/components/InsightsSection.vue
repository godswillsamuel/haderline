<template>
  <section id="insights" class="insights">

    <!-- Background -->
    <div class="insights__bg" aria-hidden="true">
      <div class="insights__bg-glow"></div>
      <div class="insights__bg-grid"></div>
    </div>

    <div class="insights__container">

      <!-- Header row -->
      <div class="insights__header">
        <div class="insights__header-left">
          <div class="insights__eyebrow">
            <span class="insights__eyebrow-line"></span>
            <span>Market Intelligence</span>
          </div>
          <h2 class="insights__heading">
            <span class="insights__heading-line">Latest</span>
            <span class="insights__heading-line insights__heading-line--ghost">Insights &</span>
            <span class="insights__heading-line insights__heading-line--coral">Analysis.</span>
          </h2>
        </div>
        <div class="insights__header-right">
          <p class="insights__header-sub">
            Our research team publishes weekly market commentary, macro outlooks,
            and investment analysis to keep our clients informed and ahead.
          </p>
          <a href="#" class="insights__all-link">
            View All Insights
            <svg width="14" height="14" viewBox="0 0 14 14" fill="none">
              <path d="M2 7h10M8 3l4 4-4 4" stroke="currentColor" stroke-width="1.4" stroke-linecap="round" stroke-linejoin="round"/>
            </svg>
          </a>
        </div>
      </div>

      <!-- Featured + side cards -->
      <div class="insights__grid">

        <!-- Featured article -->
        <article class="insights__featured" @mouseenter="featHover = true" @mouseleave="featHover = false">
          <div class="insights__featured-visual">
            <svg viewBox="0 0 600 360" fill="none" xmlns="http://www.w3.org/2000/svg" class="insights__feat-svg">
              <rect width="600" height="360" fill="#111"/>
              <!-- Grid -->
              <line x1="0" y1="72" x2="600" y2="72" stroke="rgba(255,255,255,0.04)" stroke-width="1"/>
              <line x1="0" y1="144" x2="600" y2="144" stroke="rgba(255,255,255,0.04)" stroke-width="1"/>
              <line x1="0" y1="216" x2="600" y2="216" stroke="rgba(255,255,255,0.04)" stroke-width="1"/>
              <line x1="0" y1="288" x2="600" y2="288" stroke="rgba(255,255,255,0.04)" stroke-width="1"/>
              <!-- Area fill -->
              <path d="M0,280 C60,260 100,240 160,200 C220,160 260,180 320,140 C380,100 420,120 480,80 C520,56 560,48 600,40 L600,360 L0,360 Z" fill="url(#featGrad)"/>
              <defs>
                <linearGradient id="featGrad" x1="0" y1="0" x2="0" y2="1">
                  <stop offset="0%" stop-color="#FF6B5B" stop-opacity="0.2"/>
                  <stop offset="100%" stop-color="#FF6B5B" stop-opacity="0"/>
                </linearGradient>
              </defs>
              <!-- Line -->
              <path class="insights__feat-line" d="M0,280 C60,260 100,240 160,200 C220,160 260,180 320,140 C380,100 420,120 480,80 C520,56 560,48 600,40" stroke="#FF6B5B" stroke-width="2" stroke-linecap="round" fill="none"/>
              <!-- Glow dot -->
              <circle cx="600" cy="40" r="5" fill="#FF6B5B"/>
              <circle class="insights__feat-ring" cx="600" cy="40" r="5" stroke="#FF6B5B" stroke-width="1.5" fill="none"/>
              <!-- Label -->
              <text x="30" y="340" font-size="9" fill="rgba(255,255,255,0.2)" font-family="DM Sans,sans-serif" letter-spacing="3">GLOBAL EQUITY INDEX — YTD PERFORMANCE</text>
            </svg>
            <div class="insights__featured-overlay"></div>
          </div>

          <div class="insights__featured-body">
            <div class="insights__meta">
              <span class="insights__tag insights__tag--macro">Macro</span>
              <span class="insights__date">December 12, 2024</span>
              <span class="insights__read">8 min read</span>
            </div>
            <h3 class="insights__featured-title">
              Global Equity Markets in 2025: Navigating the Rate Normalisation Cycle
            </h3>
            <p class="insights__featured-excerpt">
              As central banks across developed markets signal the end of their tightening
              cycles, equity valuations face a recalibration. Our CIO breaks down the
              sectors positioned to outperform and the risks that remain underpriced.
            </p>
            <div class="insights__featured-footer">
              <div class="insights__author">
                <span class="insights__author-avatar">JH</span>
                <div>
                  <div class="insights__author-name">James Harderlin</div>
                  <div class="insights__author-role">CIO & Founder</div>
                </div>
              </div>
              <a href="#" class="insights__read-btn">
                Read Analysis
                <svg width="14" height="14" viewBox="0 0 14 14" fill="none">
                  <path d="M2 7h10M8 3l4 4-4 4" stroke="currentColor" stroke-width="1.4" stroke-linecap="round" stroke-linejoin="round"/>
                </svg>
              </a>
            </div>
          </div>
        </article>

        <!-- Side articles -->
        <div class="insights__side">
          <article
            v-for="(article, i) in articles"
            :key="article.title"
            class="insights__card"
            :style="`--ai: ${i}`"
          >
            <div class="insights__card-top">
              <div class="insights__meta">
                <span :class="['insights__tag', `insights__tag--${article.tagClass}`]">
                  {{ article.tag }}
                </span>
                <span class="insights__date">{{ article.date }}</span>
              </div>
              <span class="insights__card-num">0{{ i + 1 }}</span>
            </div>
            <h4 class="insights__card-title">{{ article.title }}</h4>
            <p class="insights__card-excerpt">{{ article.excerpt }}</p>
            <div class="insights__card-footer">
              <span class="insights__card-author">{{ article.author }}</span>
              <a href="#" class="insights__card-link">
                Read
                <svg width="12" height="12" viewBox="0 0 12 12" fill="none">
                  <path d="M2 6h8M7 3l3 3-3 3" stroke="currentColor" stroke-width="1.3" stroke-linecap="round" stroke-linejoin="round"/>
                </svg>
              </a>
            </div>
          </article>
        </div>

      </div>

      <!-- Bottom topics bar -->
      <div class="insights__topics">
        <span class="insights__topics-label">Browse by topic:</span>
        <div class="insights__topics-list">
          <button
            v-for="topic in topics"
            :key="topic"
            :class="['insights__topic-btn', { 'insights__topic-btn--active': activeTopic === topic }]"
            @click="activeTopic = topic"
          >
            {{ topic }}
          </button>
        </div>
      </div>

    </div>
  </section>
</template>

<script>
export default {
  name: 'InsightsSection',
  data() {
    return {
      featHover: false,
      activeTopic: 'All',
      topics: ['All', 'Macro', 'Equities', 'Fixed Income', 'Private Markets', 'ESG', 'Currency'],
      articles: [
        {
          tag: 'Fixed Income',
          tagClass: 'fixed',
          date: 'Dec 8, 2024',
          title: 'The Case for Investment-Grade Credit in a Soft Landing Scenario',
          excerpt: 'Spreads remain attractive relative to historical averages as default risk recedes. We outline our positioning across IG corporate bonds.',
          author: 'Rachel Stern',
        },
        {
          tag: 'Equities',
          tagClass: 'equities',
          date: 'Dec 4, 2024',
          title: 'Emerging Market Equities: Undervalued or a Value Trap?',
          excerpt: 'With EM equities trading at a 35% discount to developed peers, we assess whether the discount reflects structural headwinds or genuine opportunity.',
          author: 'Amara Osei',
        },
        {
          tag: 'Private Markets',
          tagClass: 'private',
          date: 'Nov 28, 2024',
          title: 'Infrastructure as a Hedge: Why Real Assets Belong in Every Portfolio',
          excerpt: 'Inflation-linked cash flows and low correlation to public markets make infrastructure an increasingly compelling allocation for long-term investors.',
          author: 'James Harderlin',
        },
      ],
    };
  },
};
</script>

<style scoped>

/* ─── Section ───────────────────────────────────── */
.insights {
  position: relative;
  padding-block: var(--section-pad);
  background: var(--grey-900);
  overflow: hidden;
}

/* ─── Background ────────────────────────────────── */
.insights__bg { position: absolute; inset: 0; pointer-events: none; }

.insights__bg-glow {
  position: absolute;
  right: 5%;
  top: 20%;
  width: 480px;
  height: 480px;
  background: radial-gradient(circle, rgba(255,107,91,0.07) 0%, transparent 65%);
  border-radius: 50%;
}

.insights__bg-grid {
  position: absolute;
  inset: 0;
  background-image: radial-gradient(rgba(255,255,255,0.03) 1px, transparent 1px);
  background-size: 36px 36px;
  mask-image: radial-gradient(ellipse 80% 80% at 50% 50%, black, transparent);
}

/* ─── Container ─────────────────────────────────── */
.insights__container {
  position: relative;
  z-index: 1;
  max-width: var(--max-width);
  margin: 0 auto;
  padding-inline: clamp(24px, 5vw, 80px);
}

/* ─── Header ────────────────────────────────────── */
.insights__header {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 48px;
  align-items: flex-end;
  margin-bottom: clamp(40px, 6vw, 64px);
}

.insights__eyebrow {
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

.insights__eyebrow-line {
  display: block;
  width: 32px;
  height: 1px;
  background: var(--coral);
  flex-shrink: 0;
}

.insights__heading {
  display: flex;
  flex-direction: column;
  gap: 2px;
  font-family: var(--font-display);
  font-size: clamp(2.2rem, 4vw, 3.6rem);
  font-weight: 700;
  line-height: 1.1;
  letter-spacing: -0.02em;
}

.insights__heading-line       { color: var(--white); }
.insights__heading-line--ghost {
  color: transparent;
  -webkit-text-stroke: 1.5px rgba(255,255,255,0.2);
}
.insights__heading-line--coral { color: var(--coral); }

.insights__header-sub {
  font-size: 0.88rem;
  line-height: 1.8;
  color: var(--grey-400);
  margin-bottom: 20px;
  max-width: 420px;
}

.insights__all-link {
  display: inline-flex;
  align-items: center;
  gap: 8px;
  font-size: 0.78rem;
  font-weight: 500;
  letter-spacing: 0.1em;
  text-transform: uppercase;
  color: var(--coral);
  text-decoration: none;
  transition: gap 0.25s var(--ease);
}

.insights__all-link:hover { gap: 12px; color: var(--coral); }

/* ─── Grid ──────────────────────────────────────── */
.insights__grid {
  display: grid;
  grid-template-columns: 1.1fr 0.9fr;
  gap: 2px;
  background: rgba(255,255,255,0.06);
  border: 1px solid rgba(255,255,255,0.07);
  border-radius: 12px;
  overflow: hidden;
  margin-bottom: 28px;
}

/* ─── Featured ──────────────────────────────────── */
.insights__featured {
  background: var(--grey-950);
  display: flex;
  flex-direction: column;
  cursor: pointer;
  transition: background 0.35s var(--ease);
}

.insights__featured:hover {
  background: rgba(255,107,91,0.03);
}

.insights__featured-visual {
  position: relative;
  overflow: hidden;
  flex-shrink: 0;
}

.insights__feat-svg {
  display: block;
  width: 100%;
  height: auto;
}

.insights__feat-line {
  stroke-dasharray: 800;
  stroke-dashoffset: 800;
  animation: lineDraw 2s 0.5s var(--ease) forwards;
}

@keyframes lineDraw { to { stroke-dashoffset: 0; } }

.insights__feat-ring {
  animation: ringPulse 2.5s 2.5s ease-in-out infinite;
}

@keyframes ringPulse {
  0%, 100% { r: 5;  opacity: 0.6; }
  50%       { r: 14; opacity: 0; }
}

.insights__featured-overlay {
  position: absolute;
  inset: 0;
  background: linear-gradient(to bottom, transparent 40%, var(--grey-950) 100%);
  transition: background 0.35s;
}

.insights__featured:hover .insights__featured-overlay {
  background: linear-gradient(to bottom, transparent 40%, rgba(20,10,10,0.98) 100%);
}

.insights__featured-body {
  padding: 28px 32px 32px;
  display: flex;
  flex-direction: column;
  gap: 14px;
  flex: 1;
}

/* ─── Side cards ────────────────────────────────── */
.insights__side {
  display: flex;
  flex-direction: column;
  gap: 2px;
  background: rgba(255,255,255,0.04);
}

.insights__card {
  background: var(--grey-900);
  padding: 24px 26px;
  display: flex;
  flex-direction: column;
  gap: 10px;
  flex: 1;
  cursor: pointer;
  transition: background 0.3s var(--ease);
  border-bottom: 1px solid rgba(255,255,255,0.05);
}

.insights__card:last-child { border-bottom: none; }

.insights__card:hover {
  background: rgba(255,107,91,0.04);
}

.insights__card-top {
  display: flex;
  align-items: center;
  justify-content: space-between;
}

.insights__card-num {
  font-family: var(--font-display);
  font-size: 0.65rem;
  letter-spacing: 0.18em;
  color: rgba(255,107,91,0.3);
}

/* ─── Shared meta ───────────────────────────────── */
.insights__meta {
  display: flex;
  align-items: center;
  gap: 10px;
  flex-wrap: wrap;
}

.insights__tag {
  font-size: 0.6rem;
  font-weight: 600;
  letter-spacing: 0.12em;
  text-transform: uppercase;
  padding: 3px 10px;
  border-radius: 20px;
}

.insights__tag--macro   { color: #f59e0b; background: rgba(245,158,11,0.1);  border: 1px solid rgba(245,158,11,0.2); }
.insights__tag--fixed   { color: #60a5fa; background: rgba(96,165,250,0.1);  border: 1px solid rgba(96,165,250,0.2); }
.insights__tag--equities{ color: #4ade80; background: rgba(74,222,128,0.1);  border: 1px solid rgba(74,222,128,0.2); }
.insights__tag--private { color: var(--coral); background: rgba(255,107,91,0.1); border: 1px solid rgba(255,107,91,0.2); }

.insights__date {
  font-size: 0.68rem;
  color: var(--grey-400);
  letter-spacing: 0.05em;
}

.insights__read {
  font-size: 0.68rem;
  color: rgba(255,255,255,0.25);
  letter-spacing: 0.05em;
}

/* ─── Titles ────────────────────────────────────── */
.insights__featured-title {
  font-family: var(--font-display);
  font-size: clamp(1.3rem, 2.2vw, 1.8rem);
  font-weight: 700;
  color: var(--white);
  line-height: 1.25;
  letter-spacing: -0.01em;
}

.insights__featured-excerpt {
  font-size: 0.85rem;
  line-height: 1.8;
  color: var(--grey-400);
  flex: 1;
}

.insights__card-title {
  font-family: var(--font-display);
  font-size: 1rem;
  font-weight: 700;
  color: var(--white);
  line-height: 1.3;
  letter-spacing: -0.01em;
  transition: color 0.25s var(--ease);
}

.insights__card:hover .insights__card-title {
  color: var(--coral);
}

.insights__card-excerpt {
  font-size: 0.78rem;
  line-height: 1.7;
  color: var(--grey-400);
  flex: 1;
  display: -webkit-box;
  /* -webkit-line-clamp: 3; */
  -webkit-box-orient: vertical;
  overflow: hidden;
}

/* ─── Footers ───────────────────────────────────── */
.insights__featured-footer {
  display: flex;
  align-items: center;
  justify-content: space-between;
  gap: 16px;
  padding-top: 16px;
  border-top: 1px solid rgba(255,255,255,0.06);
  margin-top: auto;
}

.insights__author {
  display: flex;
  align-items: center;
  gap: 10px;
}

.insights__author-avatar {
  width: 34px;
  height: 34px;
  border-radius: 50%;
  background: rgba(255,107,91,0.12);
  border: 1px solid rgba(255,107,91,0.25);
  display: flex;
  align-items: center;
  justify-content: center;
  font-size: 0.65rem;
  font-weight: 700;
  color: var(--coral);
  flex-shrink: 0;
}

.insights__author-name {
  font-size: 0.78rem;
  font-weight: 600;
  color: var(--white);
}

.insights__author-role {
  font-size: 0.62rem;
  color: var(--grey-400);
  letter-spacing: 0.06em;
  margin-top: 1px;
}

.insights__read-btn {
  display: inline-flex;
  align-items: center;
  gap: 8px;
  padding: 9px 18px;
  background: var(--coral);
  color: var(--white);
  text-decoration: none;
  font-size: 0.72rem;
  font-weight: 500;
  letter-spacing: 0.1em;
  text-transform: uppercase;
  border-radius: var(--radius-sm);
  white-space: nowrap;
  flex-shrink: 0;
  transition: background 0.25s, transform 0.25s var(--ease);
  box-shadow: 0 4px 16px rgba(255,107,91,0.25);
}

.insights__read-btn:hover {
  background: var(--coral-dark);
  transform: translateY(-1px);
  color: var(--white);
}

.insights__card-footer {
  display: flex;
  align-items: center;
  justify-content: space-between;
  padding-top: 10px;
  border-top: 1px solid rgba(255,255,255,0.05);
  margin-top: auto;
}

.insights__card-author {
  font-size: 0.68rem;
  color: var(--grey-400);
  letter-spacing: 0.05em;
}

.insights__card-link {
  display: inline-flex;
  align-items: center;
  gap: 5px;
  font-size: 0.68rem;
  font-weight: 500;
  letter-spacing: 0.1em;
  text-transform: uppercase;
  color: var(--coral);
  text-decoration: none;
  transition: gap 0.22s var(--ease);
}

.insights__card-link:hover {
  gap: 8px;
  color: var(--coral);
}

/* ─── Topics Bar ────────────────────────────────── */
.insights__topics {
  display: flex;
  align-items: center;
  gap: 16px;
  padding: 20px 24px;
  background: rgba(255,255,255,0.02);
  border: 1px solid rgba(255,255,255,0.06);
  border-radius: 8px;
  flex-wrap: wrap;
}

.insights__topics-label {
  font-size: 0.68rem;
  letter-spacing: 0.15em;
  text-transform: uppercase;
  color: rgba(255,255,255,0.25);
  white-space: nowrap;
}

.insights__topics-list {
  display: flex;
  gap: 8px;
  flex-wrap: wrap;
}

.insights__topic-btn {
  padding: 6px 14px;
  font-size: 0.7rem;
  font-weight: 400;
  letter-spacing: 0.08em;
  text-transform: uppercase;
  color: rgba(255,255,255,0.4);
  background: none;
  border: 1px solid rgba(255,255,255,0.08);
  border-radius: 2px;
  cursor: pointer;
  transition: color 0.22s, border-color 0.22s, background 0.22s;
}

.insights__topic-btn:hover {
  color: var(--white);
  border-color: rgba(255,255,255,0.2);
}

.insights__topic-btn--active {
  color: var(--coral);
  border-color: rgba(255,107,91,0.35);
  background: rgba(255,107,91,0.06);
}

/* ─── Responsive ────────────────────────────────── */
@media (max-width: 1024px) {
  .insights__grid {
    grid-template-columns: 1fr;
  }

  .insights__side {
    flex-direction: row;
    overflow-x: auto;
  }

  .insights__card {
    min-width: 280px;
    border-bottom: none;
    border-right: 1px solid rgba(255,255,255,0.05);
  }
}

@media (max-width: 768px) {
  .insights__header {
    grid-template-columns: 1fr;
    gap: 24px;
  }

  .insights__side {
    flex-direction: column;
  }

  .insights__card {
    min-width: unset;
    border-right: none;
    border-bottom: 1px solid rgba(255,255,255,0.05);
  }
}
</style>