<template>
  <nav class="navbar" :class="{ scrolled: isScrolled }">
    <div class="navbar-inner">

      <!-- Logo -->
      <a href="/" class="logo">
        <span class="logo-mark">
          <svg width="28" height="28" viewBox="0 0 28 28" fill="none">
            <polygon points="14,2 26,8 26,20 14,26 2,20 2,8" stroke="currentColor" stroke-width="1.5" fill="none"/>
            <polygon points="14,7 21,11 21,18 14,22 7,18 7,11" fill="currentColor" opacity="0.18"/>
            <line x1="14" y1="2" x2="14" y2="26" stroke="currentColor" stroke-width="1" opacity="0.4"/>
          </svg>
        </span>
        <span class="logo-text">HARDELIN</span>
      </a>

      <!-- Desktop Links -->
      <ul class="nav-links" :class="{ open: menuOpen }">
        <li v-for="(item, i) in navItems" :key="i" class="nav-item">
          <a
            :href="item.href"
            class="nav-link"
            :class="{ active: activeItem === item.label }"
            @click="setActive(item.label)"
          >
            {{ item.label }}
            <span class="underline-bar"></span>
          </a>
          <!-- Dropdown -->
          <div v-if="item.children" class="dropdown">
            <a
              v-for="(child, j) in item.children"
              :key="j"
              :href="child.href"
              class="dropdown-item"
            >
              <span class="dropdown-icon">{{ child.icon }}</span>
              <span class="dropdown-text">
                <span class="dropdown-title">{{ child.label }}</span>
                <span class="dropdown-desc">{{ child.desc }}</span>
              </span>
            </a>
          </div>
        </li>
      </ul>

      <!-- Right Actions -->
      <div class="nav-actions">
        <a href="/login" class="btn-ghost">Log in</a>
        <a href="/signup" class="btn-primary">
          <span>Open Account</span>
          <svg width="14" height="14" viewBox="0 0 14 14" fill="none"><path d="M2 7h10M8 3l4 4-4 4" stroke="currentColor" stroke-width="1.5" stroke-linecap="round" stroke-linejoin="round"/></svg>
        </a>
      </div>

      <!-- Mobile Hamburger -->
      <button class="hamburger" @click="toggleMenu" :class="{ active: menuOpen }" aria-label="Toggle menu">
        <span></span>
        <span></span>
        <span></span>
      </button>

    </div>

    <!-- Mobile Menu -->
    <transition name="mobile-slide">
      <div v-if="menuOpen" class="mobile-menu">
        <a
          v-for="(item, i) in navItems"
          :key="i"
          :href="item.href"
          class="mobile-link"
          @click="menuOpen = false"
        >{{ item.label }}</a>
        <div class="mobile-divider"></div>
        <a href="/login" class="mobile-link subtle">Log in</a>
        <a href="/signup" class="mobile-cta">Open Account →</a>
      </div>
    </transition>
  </nav>
</template>

<script setup>
import { ref, onMounted, onUnmounted } from 'vue'

const isScrolled = ref(false)
const menuOpen = ref(false)
const activeItem = ref('Markets')

const navItems = [
  {
    label: 'Markets',
    href: '/markets',
    children: [
      { label: 'Equities', desc: 'Global stock markets', href: '/markets/equities', icon: '📈' },
      { label: 'Fixed Income', desc: 'Bonds & treasuries', href: '/markets/bonds', icon: '🏦' },
      { label: 'Commodities', desc: 'Gold, oil, and more', href: '/markets/commodities', icon: '🛢️' },
      { label: 'Forex', desc: 'Currency exchange', href: '/markets/forex', icon: '💱' },
    ]
  },
  {
    label: 'Portfolio',
    href: '/portfolio',
  },
  {
    label: 'Research',
    href: '/research',
    children: [
      { label: 'Insights', desc: 'Market commentary', href: '/research/insights', icon: '💡' },
      { label: 'Reports', desc: 'Deep-dive analyses', href: '/research/reports', icon: '📄' },
      { label: 'Forecasts', desc: 'Forward-looking data', href: '/research/forecasts', icon: '🔭' },
    ]
  },
  {
    label: 'Solutions',
    href: '/solutions',
  },
  {
    label: 'About',
    href: '/about',
  },
]

const setActive = (label) => {
  activeItem.value = label
  menuOpen.value = false
}

const toggleMenu = () => {
  menuOpen.value = !menuOpen.value
}

const handleScroll = () => {
  isScrolled.value = window.scrollY > 20
}

onMounted(() => window.addEventListener('scroll', handleScroll))
onUnmounted(() => window.removeEventListener('scroll', handleScroll))
</script>

<style scoped>
@import url('https://fonts.googleapis.com/css2?family=Cormorant+Garamond:wght@400;500;600&family=DM+Sans:wght@300;400;500&display=swap');

:root {
  --ink: #0d0e12;
  --parchment: #f5f2ed;
  --gold: #b8933f;
  --gold-light: #d4aa5f;
  --muted: #6b6860;
  --border: rgba(184, 147, 63, 0.2);
  --glass: rgba(245, 242, 237, 0.92);
}

* { box-sizing: border-box; margin: 0; padding: 0; }

.navbar {
  position: fixed;
  top: 0;
  left: 0;
  right: 0;
  z-index: 100;
  font-family: 'DM Sans', sans-serif;
  transition: background 0.4s ease, box-shadow 0.4s ease, padding 0.3s ease;
  background: transparent;
  padding: 0 2rem;
}

.navbar.scrolled {
  background: var(--glass);
  backdrop-filter: blur(18px) saturate(180%);
  -webkit-backdrop-filter: blur(18px) saturate(180%);
  box-shadow: 0 1px 0 var(--border), 0 8px 32px rgba(13, 14, 18, 0.08);
}

.navbar-inner {
  max-width: 1280px;
  margin: 0 auto;
  height: 72px;
  display: flex;
  align-items: center;
  gap: 2.5rem;
}

/* ─── Logo ─── */
.logo {
  display: flex;
  align-items: center;
  gap: 0.65rem;
  text-decoration: none;
  flex-shrink: 0;
}

.logo-mark {
  color: var(--gold);
  display: flex;
  align-items: center;
}

.logo-text {
  font-family: 'Cormorant Garamond', serif;
  font-size: 1.35rem;
  font-weight: 600;
  letter-spacing: 0.22em;
  color: var(--ink);
}

/* ─── Nav Links ─── */
.nav-links {
  display: flex;
  list-style: none;
  align-items: center;
  gap: 0.25rem;
  margin-left: auto;
}

.nav-item {
  position: relative;
}

.nav-link {
  display: block;
  padding: 0.5rem 0.85rem;
  font-size: 0.835rem;
  font-weight: 400;
  letter-spacing: 0.04em;
  color: var(--ink);
  text-decoration: none;
  position: relative;
  transition: color 0.2s ease;
}

.nav-link .underline-bar {
  position: absolute;
  bottom: 2px;
  left: 0.85rem;
  right: 0.85rem;
  height: 1px;
  background: var(--gold);
  transform: scaleX(0);
  transform-origin: left;
  transition: transform 0.25s ease;
}

.nav-link:hover,
.nav-link.active {
  color: var(--gold);
}

.nav-link:hover .underline-bar,
.nav-link.active .underline-bar {
  transform: scaleX(1);
}

/* ─── Dropdown ─── */
.dropdown {
  position: absolute;
  top: calc(100% + 12px);
  left: 50%;
  transform: translateX(-50%);
  background: #fff;
  border: 1px solid var(--border);
  border-radius: 10px;
  padding: 0.6rem;
  min-width: 240px;
  box-shadow: 0 16px 48px rgba(13, 14, 18, 0.12);
  display: none;
  flex-direction: column;
  gap: 2px;
}

.nav-item:hover .dropdown {
  display: flex;
  animation: dropIn 0.18s ease;
}

@keyframes dropIn {
  from { opacity: 0; transform: translateX(-50%) translateY(-6px); }
  to   { opacity: 1; transform: translateX(-50%) translateY(0); }
}

.dropdown-item {
  display: flex;
  align-items: center;
  gap: 0.75rem;
  padding: 0.65rem 0.75rem;
  border-radius: 7px;
  text-decoration: none;
  transition: background 0.15s ease;
}

.dropdown-item:hover {
  background: #faf8f5;
}

.dropdown-icon {
  font-size: 1.1rem;
  width: 28px;
  text-align: center;
  flex-shrink: 0;
}

.dropdown-text {
  display: flex;
  flex-direction: column;
  gap: 1px;
}

.dropdown-title {
  font-size: 0.83rem;
  font-weight: 500;
  color: var(--ink);
  letter-spacing: 0.02em;
}

.dropdown-desc {
  font-size: 0.73rem;
  color: var(--muted);
}

/* ─── Actions ─── */
.nav-actions {
  display: flex;
  align-items: center;
  gap: 0.75rem;
  flex-shrink: 0;
}

.btn-ghost {
  font-family: 'DM Sans', sans-serif;
  font-size: 0.835rem;
  font-weight: 400;
  letter-spacing: 0.03em;
  color: var(--ink);
  text-decoration: none;
  padding: 0.45rem 0.9rem;
  border-radius: 6px;
  transition: color 0.2s ease, background 0.2s ease;
}

.btn-ghost:hover {
  color: var(--gold);
  background: rgba(184, 147, 63, 0.06);
}

.btn-primary {
  display: flex;
  align-items: center;
  gap: 0.5rem;
  font-family: 'DM Sans', sans-serif;
  font-size: 0.835rem;
  font-weight: 500;
  letter-spacing: 0.04em;
  color: #fff;
  text-decoration: none;
  background: var(--ink);
  padding: 0.5rem 1.1rem;
  border-radius: 6px;
  border: 1px solid var(--ink);
  transition: background 0.2s ease, color 0.2s ease, border-color 0.2s ease;
}

.btn-primary:hover {
  background: var(--gold);
  border-color: var(--gold);
}

.btn-primary svg {
  transition: transform 0.2s ease;
}

.btn-primary:hover svg {
  transform: translateX(3px);
}

/* ─── Hamburger ─── */
.hamburger {
  display: none;
  flex-direction: column;
  gap: 5px;
  background: none;
  border: none;
  cursor: pointer;
  padding: 6px;
  margin-left: auto;
}

.hamburger span {
  display: block;
  height: 1.5px;
  width: 24px;
  background: var(--ink);
  transition: transform 0.3s ease, opacity 0.3s ease;
  transform-origin: center;
}

.hamburger.active span:nth-child(1) { transform: translateY(6.5px) rotate(45deg); }
.hamburger.active span:nth-child(2) { opacity: 0; }
.hamburger.active span:nth-child(3) { transform: translateY(-6.5px) rotate(-45deg); }

/* ─── Mobile Menu ─── */
.mobile-menu {
  display: flex;
  flex-direction: column;
  padding: 1rem 1.5rem 1.5rem;
  border-top: 1px solid var(--border);
  background: var(--glass);
  backdrop-filter: blur(18px);
}

.mobile-link {
  font-size: 0.9rem;
  font-weight: 400;
  color: var(--ink);
  text-decoration: none;
  padding: 0.75rem 0;
  border-bottom: 1px solid rgba(184, 147, 63, 0.1);
  letter-spacing: 0.03em;
  transition: color 0.2s ease;
}

.mobile-link:hover { color: var(--gold); }
.mobile-link.subtle { color: var(--muted); }

.mobile-divider {
  height: 1rem;
}

.mobile-cta {
  margin-top: 0.75rem;
  display: inline-flex;
  align-items: center;
  justify-content: center;
  background: var(--ink);
  color: #fff;
  text-decoration: none;
  font-size: 0.875rem;
  font-weight: 500;
  letter-spacing: 0.05em;
  padding: 0.8rem 1.5rem;
  border-radius: 7px;
  transition: background 0.2s ease;
}

.mobile-cta:hover { background: var(--gold); }

/* ─── Transitions ─── */
.mobile-slide-enter-active,
.mobile-slide-leave-active {
  transition: opacity 0.25s ease, transform 0.25s ease;
}
.mobile-slide-enter-from,
.mobile-slide-leave-to {
  opacity: 0;
  transform: translateY(-8px);
}

/* ─── Responsive ─── */
@media (max-width: 900px) {
  .nav-links, .nav-actions { display: none; }
  .hamburger { display: flex; }
  .navbar-inner { gap: 1rem; }
}
</style>