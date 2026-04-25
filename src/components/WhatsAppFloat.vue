<template>
  <a
    href="https://wa.me/419634916797"
    target="_blank"
    rel="noopener noreferrer"
    class="wa-float"
    aria-label="Chat with us on WhatsApp"
  >
    <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 32 32" fill="none">
      <circle cx="16" cy="16" r="16" fill="#25D366"/>
      <path fill="#fff" d="M22.9 9.07A9.7 9.7 0 0 0 16.04 6C10.52 6 6.04 10.48 6.04 16a9.94 9.94 0 0 0 1.33 4.97L6 26l5.18-1.36A9.95 9.95 0 0 0 16.04 26c5.52 0 10-4.48 10-10a9.93 9.93 0 0 0-3.14-6.93Zm-6.86 15.38a8.27 8.27 0 0 1-4.22-1.15l-.3-.18-3.08.81.82-3-.2-.31A8.3 8.3 0 0 1 7.7 16c0-4.6 3.74-8.34 8.34-8.34a8.28 8.28 0 0 1 8.33 8.34c0 4.6-3.73 8.35-8.33 8.35Zm4.57-6.24c-.25-.12-1.47-.72-1.7-.81-.23-.08-.39-.12-.56.13-.17.25-.64.81-.79.97-.14.17-.29.19-.54.06-.25-.12-1.04-.38-1.98-1.22a7.46 7.46 0 0 1-1.37-1.71c-.14-.25-.01-.38.11-.5.11-.11.25-.29.37-.43.13-.14.17-.25.25-.41.08-.17.04-.31-.02-.43-.06-.13-.56-1.34-.76-1.83-.2-.48-.4-.41-.56-.42h-.47c-.17 0-.43.06-.66.31-.22.25-.87.85-.87 2.07 0 1.22.89 2.4 1.01 2.57.13.16 1.75 2.67 4.24 3.74.59.26 1.05.41 1.41.52.59.19 1.13.16 1.56.1.47-.07 1.46-.6 1.67-1.17.2-.58.2-1.07.14-1.17-.06-.1-.22-.16-.47-.28Z"/>
    </svg>
    <span class="wa-tooltip">Chat with us</span>
  </a>
</template>

<script setup>
</script>

<style scoped>
.wa-float {
  position: fixed;
  bottom: 2rem;
  right: 2rem;
  width: 56px;
  height: 56px;
  border-radius: 50%;
  display: flex;
  align-items: center;
  justify-content: center;
  box-shadow: 0 4px 20px rgba(37, 211, 102, 0.4), 0 2px 8px rgba(0,0,0,0.15);
  z-index: 999;
  text-decoration: none;
  transition: transform 0.25s ease, box-shadow 0.25s ease;
  animation: pulse 2.5s infinite;
}

.wa-float svg {
  width: 56px;
  height: 56px;
  border-radius: 50%;
}

.wa-float:hover {
  transform: scale(1.1);
  box-shadow: 0 6px 28px rgba(37, 211, 102, 0.55), 0 4px 12px rgba(0,0,0,0.18);
  animation: none;
}

/* Tooltip */
.wa-tooltip {
  position: absolute;
  right: calc(100% + 12px);
  background: #111;
  color: #fff;
  font-family: 'DM Sans', sans-serif;
  font-size: 0.78rem;
  letter-spacing: 0.03em;
  white-space: nowrap;
  padding: 0.35rem 0.75rem;
  border-radius: 5px;
  opacity: 0;
  pointer-events: none;
  transform: translateX(6px);
  transition: opacity 0.2s ease, transform 0.2s ease;
}

.wa-tooltip::after {
  content: '';
  position: absolute;
  left: 100%;
  top: 50%;
  transform: translateY(-50%);
  border: 5px solid transparent;
  border-left-color: #111;
}

.wa-float:hover .wa-tooltip {
  opacity: 1;
  transform: translateX(0);
}

/* Pulse animation */
@keyframes pulse {
  0%   { box-shadow: 0 0 0 0 rgba(37, 211, 102, 0.5); }
  70%  { box-shadow: 0 0 0 12px rgba(37, 211, 102, 0); }
  100% { box-shadow: 0 0 0 0 rgba(37, 211, 102, 0); }
}
</style>