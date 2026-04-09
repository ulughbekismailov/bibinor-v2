<template>
  <header :class="['navbar', { scrolled: isScrolled, 'menu-open': menuOpen }]">
    <div class="nav-container">
      <RouterLink to="/" class="logo" @click="menuOpen = false">
        <span class="logo-text">BIBINOR</span>
        <span class="logo-sub">PHARMACEUTICALS</span>
      </RouterLink>

      <nav class="nav-links">
        <RouterLink to="/" exact-active-class="active">Главная</RouterLink>
        <RouterLink to="/about" active-class="active">О компании</RouterLink>
        <RouterLink to="/products" active-class="active">Препараты</RouterLink>
        <RouterLink to="/certificates" active-class="active">Сертификаты</RouterLink>
        <RouterLink to="/contact" active-class="active">Контакты</RouterLink>
      </nav>

      <a href="tel:+998995203040" class="nav-phone">
        <svg width="14" height="14" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2">
          <path d="M22 16.92v3a2 2 0 01-2.18 2 19.79 19.79 0 01-8.63-3.07A19.5 19.5 0 014.5 11.5a19.79 19.79 0 01-3.07-8.67A2 2 0 013.44 1h3a2 2 0 012 1.72c.127.96.361 1.903.7 2.81a2 2 0 01-.45 2.11L7.91 8.91a16 16 0 006.29 6.29l1.28-1.28a2 2 0 012.11-.45c.907.339 1.85.573 2.81.7A2 2 0 0122 16.92z"/>
        </svg>
        +998 995-20-30-40
      </a>

      <button class="burger" @click="menuOpen = !menuOpen" :aria-expanded="menuOpen">
        <span></span><span></span><span></span>
      </button>
    </div>

    <!-- Mobile menu -->
    <div class="mobile-menu" :class="{ open: menuOpen }">
      <RouterLink to="/" @click="menuOpen = false">Главная</RouterLink>
      <RouterLink to="/about" @click="menuOpen = false">О компании</RouterLink>
      <RouterLink to="/products" @click="menuOpen = false">Препараты</RouterLink>
      <RouterLink to="/certificates" @click="menuOpen = false">Сертификаты</RouterLink>
      <RouterLink to="/contact" @click="menuOpen = false">Контакты</RouterLink>
      <a href="tel:+998995203040" class="mob-phone">+998 99 520 30 40</a>
    </div>
  </header>
</template>

<script setup>
import { ref, onMounted, onUnmounted } from 'vue'

const isScrolled = ref(false)
const menuOpen = ref(false)

const handleScroll = () => {
  isScrolled.value = window.scrollY > 50
}

onMounted(() => window.addEventListener('scroll', handleScroll))
onUnmounted(() => window.removeEventListener('scroll', handleScroll))
</script>

<style scoped>
.navbar {
  position: fixed;
  top: 0;
  left: 0;
  right: 0;
  z-index: 1000;
  transition: all 0.4s ease;
  background: transparent;
}

.navbar.scrolled {
  background: var(--navy);
  box-shadow: 0 2px 40px rgba(0,0,0,0.3);
}

.nav-container {
  max-width: 1280px;
  margin: 0 auto;
  padding: 0 40px;
  display: flex;
  align-items: center;
  height: 80px;
  gap: 40px;
}

.logo {
  display: flex;
  flex-direction: column;
  line-height: 1;
  text-decoration: none;
}

.logo-text {
  font-family: 'Cormorant Garamond', serif;
  font-size: 26px;
  font-weight: 700;
  color: var(--white);
  letter-spacing: 4px;
}

.logo-sub {
  font-family: 'Jost', sans-serif;
  font-size: 8px;
  font-weight: 500;
  letter-spacing: 5px;
  color: var(--gold);
  text-transform: uppercase;
  margin-top: 2px;
}

.nav-links {
  display: flex;
  gap: 36px;
  margin-left: auto;
}

.nav-links a {
  font-size: 12px;
  font-weight: 500;
  letter-spacing: 2px;
  text-transform: uppercase;
  color: rgba(255,255,255,0.8);
  text-decoration: none;
  transition: color 0.3s;
  position: relative;
  padding-bottom: 4px;
}

.nav-links a::after {
  content: '';
  position: absolute;
  bottom: 0;
  left: 0;
  width: 0;
  height: 1px;
  background: var(--gold);
  transition: width 0.3s;
}

.nav-links a:hover,
.nav-links a.active {
  color: var(--gold);
}

.nav-links a:hover::after,
.nav-links a.active::after {
  width: 100%;
}

.nav-phone {
  display: flex;
  align-items: center;
  gap: 8px;
  font-size: 12px;
  font-weight: 500;
  letter-spacing: 1px;
  color: var(--gold);
  text-decoration: none;
  border: 1px solid rgba(201,168,76,0.3);
  padding: 8px 16px;
  transition: all 0.3s;
  white-space: nowrap;
}

.nav-phone:hover {
  background: var(--gold);
  color: var(--navy);
  border-color: var(--gold);
}

.burger {
  display: none;
  flex-direction: column;
  gap: 5px;
  background: none;
  border: none;
  cursor: pointer;
  padding: 4px;
  margin-left: auto;
}

.burger span {
  display: block;
  width: 24px;
  height: 2px;
  background: var(--white);
  transition: all 0.3s;
}

.mobile-menu {
  display: none;
  flex-direction: column;
  background: var(--navy);
  padding: 20px 40px 30px;
  gap: 4px;
  max-height: 0;
  overflow: hidden;
  transition: max-height 0.4s ease;
}

.mobile-menu.open {
  max-height: 400px;
}

.mobile-menu a {
  font-size: 13px;
  font-weight: 500;
  letter-spacing: 2px;
  text-transform: uppercase;
  color: rgba(255,255,255,0.7);
  text-decoration: none;
  padding: 12px 0;
  border-bottom: 1px solid rgba(255,255,255,0.07);
  transition: color 0.3s;
}

.mobile-menu a:hover { color: var(--gold); }

.mob-phone {
  color: var(--gold) !important;
  border: none !important;
  margin-top: 8px;
}

@media (max-width: 1024px) {
  .nav-links { gap: 24px; }
  .nav-phone { display: none; }
}

@media (max-width: 768px) {
  .nav-links { display: none; }
  .burger { display: flex; }
  .mobile-menu { display: flex; }
  .navbar.menu-open { background: var(--navy); }
}
</style>
