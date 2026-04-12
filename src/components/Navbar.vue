<template>
  <header :class="['navbar', { 'navbar--scrolled': isScrolled }]">
    <div class="navbar__accent-line"></div>

    <nav class="navbar__inner">
      <!-- Logo -->
      <a href="#" class="navbar__logo" @mouseenter="logoHover = true" @mouseleave="logoHover = false">
        <span class="navbar__logo-mark">
          <svg width="32" height="32" viewBox="0 0 32 32" fill="none">
            <polygon class="logo-poly" points="16,2 30,10 30,22 16,30 2,22 2,10" stroke="#FF6B5B" stroke-width="2" fill="none"/>
            <polygon class="logo-poly logo-poly--inner" points="16,8 24,13 24,19 16,24 8,19 8,13" fill="#FF6B5B" opacity="0.18"/>
            <line x1="16" y1="2" x2="16" y2="30" stroke="#FF6B5B" stroke-width="1" opacity="0.4"/>
            <line x1="2" y1="10" x2="30" y2="22" stroke="#FF6B5B" stroke-width="1" opacity="0.4"/>
            <line x1="30" y1="10" x2="2" y2="22" stroke="#FF6B5B" stroke-width="1" opacity="0.4"/>
          </svg>
        </span>
        <span class="navbar__logo-text">
          <span class="navbar__logo-name">Harderlin</span>
          <span class="navbar__logo-sub">Investment Group</span>
        </span>
      </a>

      <!-- Desktop Nav Links -->
      <ul class="navbar__links">
        <li
          v-for="(item, i) in navItems"
          :key="item.label"
          class="navbar__link-item"
          :style="`--i: ${i}`"
        >
          <a
            :href="item.href"
            class="navbar__link"
            :class="{ 'navbar__link--active': activeLink === item.label }"
            @click="setActive(item.label)"
          >
            <!-- Split each letter for the character-swap effect -->
            <span class="navbar__link-inner" aria-hidden="true">
              <span
                v-for="(char, ci) in item.label.split('')"
                :key="ci"
                class="navbar__link-char"
                :style="`--ci: ${ci}`"
              >{{ char }}</span>
            </span>
            <!-- Accessible real text hidden visually -->
            <span class="navbar__link-real">{{ item.label }}</span>
          </a>
        </li>
      </ul>

      <!-- CTA Button -->
      <div class="navbar__actions">
        <a href="#" class="navbar__cta">
          <span class="navbar__cta-label">Get Started</span>
          <span class="navbar__cta-arrow">
            <svg width="14" height="14" viewBox="0 0 14 14" fill="none">
              <path d="M1 7h12M8 2l5 5-5 5" stroke="currentColor" stroke-width="1.4" stroke-linecap="round" stroke-linejoin="round"/>
            </svg>
          </span>
        </a>
      </div>

      <!-- Mobile Hamburger -->
      <button class="navbar__hamburger" @click="toggleMenu" :aria-expanded="menuOpen" aria-label="Toggle menu">
        <span class="navbar__bar" :class="{ 'navbar__bar--top-open': menuOpen }"></span>
        <span class="navbar__bar" :class="{ 'navbar__bar--mid-open': menuOpen }"></span>
        <span class="navbar__bar" :class="{ 'navbar__bar--bot-open': menuOpen }"></span>
      </button>
    </nav>

    <!-- Mobile Menu -->
    <transition name="mobile-menu">
      <div v-if="menuOpen" class="navbar__mobile-menu">
        <ul class="navbar__mobile-links">
          <li
            v-for="(item, i) in navItems"
            :key="item.label"
            class="navbar__mobile-item"
            :style="`--delay: ${0.08 * (i + 1)}s`"
          >
            <a :href="item.href" class="navbar__mobile-link" @click="menuOpen = false">
              <span class="navbar__mobile-num">0{{ i + 1 }}</span>
              {{ item.label }}
            </a>
          </li>
        </ul>
        <a href="#" class="navbar__mobile-cta" @click="menuOpen = false">Get Started →</a>
        <div class="navbar__mobile-deco"></div>
      </div>
    </transition>
  </header>
</template>

<script>
export default {
  name: 'Navbar',
  data() {
    return {
      isScrolled: false,
      menuOpen: false,
      logoHover: false,
      activeLink: 'Home',
      navItems: [
        { label: 'Home',     href: '#home' },
        { label: 'About',    href: '#about' },
        { label: 'Services', href: '#services' },
        { label: 'Insights', href: '#insights' },
        { label: 'Contact',  href: '#contact' },
      ],
    };
  },
  mounted() {
    window.addEventListener('scroll', this.handleScroll);
  },
  beforeUnmount() {
    window.removeEventListener('scroll', this.handleScroll);
  },
  methods: {
    handleScroll() {
      this.isScrolled = window.scrollY > 40;
    },
    toggleMenu() {
      this.menuOpen = !this.menuOpen;
    },
    setActive(label) {
      this.activeLink = label;
    },
  },
};
</script>

<style scoped>

/* ─── Navbar Shell ──────────────────────────────── */
.navbar {
  position: fixed;
  top: 0; left: 0; right: 0;
  z-index: var(--z-nav);
  font-family: var(--font-body);
  background: transparent;
  transition: background 0.45s var(--ease), box-shadow 0.45s var(--ease);
}

.navbar--scrolled {
  background: rgba(17, 17, 17, 0.94);
  backdrop-filter: blur(24px);
  -webkit-backdrop-filter: blur(24px);
  box-shadow: 0 1px 0 rgba(255, 107, 91, 0.12),
              0 12px 40px rgba(0, 0, 0, 0.35);
}

/* ─── Accent Line ───────────────────────────────── */
.navbar__accent-line {
  position: absolute;
  top: 0; left: 0; right: 0;
  height: 2px;
  background: linear-gradient(90deg, transparent, #FF6B5B 40%, #FF9A8B 60%, transparent);
  background-size: 200% 100%;
  transform-origin: left;
  transform: scaleX(0);
  animation: lineIn 0.9s 0.3s var(--ease) forwards,
             shimmer 4s 1.2s ease-in-out infinite;
}

@keyframes lineIn  { to { transform: scaleX(1); } }
@keyframes shimmer {
  0%   { background-position: 200% 0; }
  100% { background-position: -200% 0; }
}

/* ─── Inner ─────────────────────────────────────── */
.navbar__inner {
  display: flex;
  align-items: center;
  justify-content: space-between;
  max-width: var(--max-width);
  margin: 0 auto;
  padding: 0 40px;
  height: var(--nav-height);
  transition: height 0.35s var(--ease);
  gap: 24px;
}

.navbar--scrolled .navbar__inner {
  height: 60px;
}

/* ─── Logo ──────────────────────────────────────── */
.navbar__logo {
  display: flex;
  align-items: center;
  gap: 12px;
  text-decoration: none;
  flex-shrink: 0;
  animation: fadeSlideDown 0.7s 0.1s var(--ease) both;
}

.navbar__logo-mark svg {
  transition: transform 0.5s var(--ease);
}
.navbar__logo:hover .navbar__logo-mark svg {
  transform: rotate(30deg) scale(1.08);
}

.logo-poly {
  stroke-dasharray: 120;
  stroke-dashoffset: 120;
  animation: drawPoly 1.2s ease-out forwards;
}
.logo-poly--inner {
  opacity: 0;
  animation: fadeInPoly 0.6s 0.9s ease forwards;
}

@keyframes drawPoly   { to { stroke-dashoffset: 0; } }
@keyframes fadeInPoly { to { opacity: 0.18; } }

.navbar__logo-text {
  display: flex;
  flex-direction: column;
  line-height: 1;
}
.navbar__logo-name {
  font-family: var(--font-display);
  font-weight: 700;
  font-size: 1.45rem;
  letter-spacing: 0.04em;
  color: var(--white);
  text-transform: uppercase;
}
.navbar__logo-sub {
  font-size: 0.58rem;
  font-weight: 300;
  letter-spacing: 0.22em;
  color: var(--coral);
  text-transform: uppercase;
  margin-top: 2px;
}

/* ─── Nav Links — Character Lift Effect ─────────── */
/*
  On hover, each letter translates upward and fades out
  while a coral-coloured clone lifts in from below.
  Achieved with a CSS-only split-char technique using
  custom property --ci (char index) for stagger timing.
*/
.navbar__links {
  display: flex;
  align-items: center;
  gap: 2px;
  list-style: none;
}

.navbar__link-item {
  animation: fadeSlideDown 0.6s calc(0.15s + var(--i) * 0.07s) var(--ease) both;
}

.navbar__link {
  position: relative;
  display: inline-block;
  padding: 8px 14px;
  text-decoration: none;
  font-size: 0.8rem;
  font-weight: 400;
  letter-spacing: 0.1em;
  text-transform: uppercase;
  overflow: hidden;
  /* Hide the real text — it's only for accessibility */
}

/* Real label: visually hidden, keeps layout width */
.navbar__link-real {
  visibility: hidden;
  display: block;
  font-size: 0.8rem;
  letter-spacing: 0.1em;
  text-transform: uppercase;
  height: 0;
  overflow: hidden;
  white-space: nowrap;
}

/* Char container: absolutely stacked over the link */
.navbar__link-inner {
  position: absolute;
  inset: 0;
  display: flex;
  align-items: center;
  justify-content: center;
  padding: 0 14px;
  gap: 0;
}

.navbar__link-char {
  display: inline-block;
  color: rgba(255, 255, 255, 0.65);
  transition:
    transform 0.28s calc(var(--ci) * 0.018s) var(--ease),
    color     0.28s calc(var(--ci) * 0.018s) var(--ease),
    opacity   0.28s calc(var(--ci) * 0.018s) var(--ease);
  will-change: transform;
  white-space: pre; /* preserve spaces */
}

/* Active state: full white, no motion needed */
.navbar__link--active .navbar__link-char {
  color: var(--white);
}

/* Active indicator: thin coral tick below the word */
.navbar__link--active::after {
  content: '';
  position: absolute;
  bottom: 5px;
  left: 50%;
  transform: translateX(-50%);
  width: 16px;
  height: 2px;
  background: var(--coral);
  border-radius: 2px;
  transition: width 0.3s var(--ease);
}

/* Hover: chars lift up and turn coral, staggered */
.navbar__link:hover .navbar__link-char {
  color: var(--coral);
  transform: translateY(-3px);
}

/* ─── CTA — Bordered Split Button ───────────────── */
/*
  Clean border button. On hover the border colour
  intensifies and the arrow slides right — no fill sweep.
*/
.navbar__actions {
  flex-shrink: 0;
  animation: fadeSlideDown 0.7s 0.55s var(--ease) both;
}

.navbar__cta {
  position: relative;
  display: inline-flex;
  align-items: center;
  gap: 10px;
  padding: 9px 20px;
  text-decoration: none;
  color: rgba(255, 255, 255, 0.8);
  font-size: 0.76rem;
  font-weight: 500;
  letter-spacing: 0.12em;
  text-transform: uppercase;
  border: 1px solid rgba(255, 107, 91, 0.45);
  border-radius: var(--radius-sm);
  transition:
    color        0.28s var(--ease),
    border-color 0.28s var(--ease),
    box-shadow   0.28s var(--ease);
}

.navbar__cta:hover {
  color: var(--white);
  border-color: var(--coral);
  box-shadow: 0 0 0 1px var(--coral),
              inset 0 0 20px rgba(255, 107, 91, 0.06);
}

.navbar__cta-arrow {
  display: flex;
  align-items: center;
  opacity: 0.6;
  transform: translateX(0);
  transition:
    transform 0.28s var(--ease),
    opacity   0.28s var(--ease);
}

.navbar__cta:hover .navbar__cta-arrow {
  transform: translateX(5px);
  opacity: 1;
}

/* ─── Divider between label and arrow ───────────── */
.navbar__cta::before {
  content: '';
  position: absolute;
  right: 38px;
  top: 25%;
  height: 50%;
  width: 1px;
  background: rgba(255, 107, 91, 0.3);
  transition: background 0.28s var(--ease);
}
.navbar__cta:hover::before {
  background: rgba(255, 107, 91, 0.6);
}

/* ─── Hamburger ─────────────────────────────────── */
.navbar__hamburger {
  display: none;
  flex-direction: column;
  justify-content: center;
  gap: 5px;
  background: none;
  border: none;
  cursor: pointer;
  padding: 8px;
  z-index: 1100;
  flex-shrink: 0;
}

.navbar__bar {
  display: block;
  width: 24px;
  height: 1.5px;
  background: var(--white);
  border-radius: 2px;
  transition: transform 0.35s var(--ease), opacity 0.25s, width 0.3s;
  transform-origin: center;
}

.navbar__bar--top-open { transform: translateY(6.5px) rotate(45deg); }
.navbar__bar--mid-open { opacity: 0; transform: scaleX(0); }
.navbar__bar--bot-open { transform: translateY(-6.5px) rotate(-45deg); }

/* ─── Mobile Menu ───────────────────────────────── */
.navbar__mobile-menu {
  position: fixed;
  inset: 0;
  background: var(--grey-900);
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: flex-start;
  padding: 80px 48px 48px;
  z-index: 1050;
  overflow: hidden;
}

.navbar__mobile-links {
  list-style: none;
  display: flex;
  flex-direction: column;
  gap: 4px;
  width: 100%;
}

.navbar__mobile-item {
  animation: mobileLinkIn 0.45s var(--delay, 0.1s) var(--ease) both;
  overflow: hidden;
}

.navbar__mobile-link {
  display: flex;
  align-items: baseline;
  gap: 16px;
  text-decoration: none;
  font-family: var(--font-display);
  font-size: clamp(2.2rem, 6vw, 3.5rem);
  font-weight: 700;
  color: var(--white);
  padding: 8px 0;
  border-bottom: 1px solid rgba(255, 255, 255, 0.06);
  transition: color 0.25s, padding-left 0.3s var(--ease);
}

.navbar__mobile-link:hover {
  color: var(--coral);
  padding-left: 12px;
}

.navbar__mobile-num {
  font-family: var(--font-body);
  font-size: 0.65rem;
  letter-spacing: 0.2em;
  color: var(--coral);
  opacity: 0.8;
  min-width: 24px;
}

.navbar__mobile-cta {
  margin-top: 40px;
  font-family: var(--font-body);
  font-size: 0.8rem;
  letter-spacing: 0.2em;
  text-transform: uppercase;
  color: var(--coral);
  text-decoration: none;
  padding: 14px 28px;
  border: 1.5px solid var(--coral);
  display: inline-block;
  transition: background 0.3s, color 0.3s;
  animation: mobileLinkIn 0.45s 0.55s var(--ease) both;
}

.navbar__mobile-cta:hover {
  background: var(--coral);
  color: var(--white);
}

.navbar__mobile-deco {
  position: absolute;
  right: -80px; bottom: -80px;
  width: 320px; height: 320px;
  border: 1px solid rgba(255, 107, 91, 0.12);
  border-radius: 50%;
  pointer-events: none;
}

.navbar__mobile-deco::before {
  content: '';
  position: absolute;
  inset: 40px;
  border: 1px solid rgba(255, 107, 91, 0.08);
  border-radius: 50%;
}

/* ─── Vue Transitions ───────────────────────────── */
.mobile-menu-enter-active {
  transition: clip-path 0.55s var(--ease), opacity 0.35s;
  clip-path: circle(0% at calc(100% - 52px) 38px);
}
.mobile-menu-enter-to {
  clip-path: circle(150% at calc(100% - 52px) 38px);
  opacity: 1;
}
.mobile-menu-leave-active {
  transition: clip-path 0.5s var(--ease), opacity 0.3s 0.1s;
}
.mobile-menu-leave-to {
  clip-path: circle(0% at calc(100% - 52px) 38px);
  opacity: 0;
}

/* ─── Keyframes ─────────────────────────────────── */
@keyframes fadeSlideDown {
  from { opacity: 0; transform: translateY(-14px); }
  to   { opacity: 1; transform: translateY(0); }
}

@keyframes mobileLinkIn {
  from { opacity: 0; transform: translateX(-20px); }
  to   { opacity: 1; transform: translateX(0); }
}

/* ─── Responsive ────────────────────────────────── */
@media (max-width: 900px) {
  .navbar__links,
  .navbar__actions { display: none; }
  .navbar__hamburger { display: flex; }
  .navbar__inner { padding: 0 24px; }
}
</style>