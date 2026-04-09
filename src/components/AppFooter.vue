<template>
  <footer class="footer">
    <div class="footer-top">
      <div class="container">
        <div class="footer-grid">
          <div class="footer-brand">
            <div class="footer-logo">
              <span class="logo-text">BIBINOR</span>
              <span class="logo-sub">PHARMACEUTICALS</span>
            </div>
            <p class="footer-desc">
              Более 25 лет мы создаём высококачественные ветеринарные препараты, которые защищают здоровье животных и поддерживают процветание хозяйств по всему Узбекистану.
            </p>
            <div class="footer-certs">
              <span class="cert-badge">GMP</span>
              <span class="cert-badge">HALAL</span>
              <span class="cert-badge">ISO</span>
            </div>
          </div>

          <div class="footer-col">
            <h4>Навигация</h4>
            <ul>
              <li><RouterLink to="/">Главная</RouterLink></li>
              <li><RouterLink to="/about">О компании</RouterLink></li>
              <li><RouterLink to="/products">Все препараты</RouterLink></li>
              <li><RouterLink to="/certificates">Сертификаты</RouterLink></li>
              <li><RouterLink to="/contact">Контакты</RouterLink></li>
            </ul>
          </div>

          <div class="footer-col">
            <h4>Препараты</h4>
            <ul>
              <li><RouterLink to="/products/dostim">ДОСТИМ</RouterLink></li>
              <li><RouterLink to="/products/immunoparazitan">ИММУНОПАРАЗИТАН</RouterLink></li>
              <li><RouterLink to="/products/imnamak">ИМНАМАК</RouterLink></li>
              <li><RouterLink to="/products/immunofor">ИММУНОФОР</RouterLink></li>
              <li><RouterLink to="/products/florabalans">ФЛОРАБАЛАНС</RouterLink></li>
            </ul>
          </div>

          <div class="footer-col">
            <h4>Контакты</h4>
            <div class="contact-items">
              <div class="contact-item">
                <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.5"><path d="M22 16.92v3a2 2 0 01-2.18 2 19.79 19.79 0 01-8.63-3.07A19.5 19.5 0 014.5 11.5a19.79 19.79 0 01-3.07-8.67A2 2 0 013.44 1h3a2 2 0 012 1.72c.127.96.361 1.903.7 2.81a2 2 0 01-.45 2.11L7.91 8.91a16 16 0 006.29 6.29l1.28-1.28a2 2 0 012.11-.45c.907.339 1.85.573 2.81.7A2 2 0 0122 16.92z"/></svg>
                <a href="tel:+998995203040">+998 99 520 30 40</a>
              </div>
              <div class="contact-item">
                <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.5"><path d="M4 4h16c1.1 0 2 .9 2 2v12c0 1.1-.9 2-2 2H4c-1.1 0-2-.9-2-2V6c0-1.1.9-2 2-2z"/><polyline points="22,6 12,13 2,6"/></svg>
                <a href="mailto:bibinorpharm@gmail.com">bibinorpharm@gmail.com</a>
              </div>
              <div class="contact-item">
                <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.5"><path d="M21 10c0 7-9 13-9 13s-9-6-9-13a9 9 0 0118 0z"/><circle cx="12" cy="10" r="3"/></svg>
                <span>Республика Узбекистан</span>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>

    <div class="footer-bottom">
      <div class="container">
        <p>© {{ new Date().getFullYear() }} BIBINOR Pharmaceuticals. Все права защищены.</p>
        <p class="footer-note">Ветеринарные препараты. Применять по назначению ветеринарного врача.</p>
      </div>
    </div>
  </footer>
</template>

<style scoped>
.footer {
  background: #14145a;
  color: rgba(255,255,255,0.7);
}

.footer-top {
  padding: 80px 0 60px;
}

.footer-grid {
  display: grid;
  grid-template-columns: 2fr 1fr 1fr 1.5fr;
  gap: 60px;
}

.footer-logo {
  display: flex;
  flex-direction: column;
  margin-bottom: 24px;
}

.logo-text {
  font-family: 'Cormorant Garamond', serif;
  font-size: 28px;
  font-weight: 700;
  color: var(--white);
  letter-spacing: 4px;
}

.logo-sub {
  font-size: 8px;
  font-weight: 500;
  letter-spacing: 5px;
  color: var(--gold);
  text-transform: uppercase;
  margin-top: 2px;
}

.footer-desc {
  font-size: 14px;
  line-height: 1.8;
  color: rgba(255,255,255,0.5);
  margin-bottom: 28px;
}

.footer-certs {
  display: flex;
  gap: 10px;
}

.cert-badge {
  font-size: 10px;
  font-weight: 700;
  letter-spacing: 2px;
  color: var(--gold);
  border: 1px solid rgba(201,168,76,0.3);
  padding: 5px 12px;
}

.footer-col h4 {
  font-family: 'Jost', sans-serif;
  font-size: 10px;
  font-weight: 600;
  letter-spacing: 3px;
  text-transform: uppercase;
  color: var(--gold);
  margin-bottom: 24px;
}

.footer-col ul {
  list-style: none;
  display: flex;
  flex-direction: column;
  gap: 12px;
}

.footer-col ul li a {
  font-size: 14px;
  color: rgba(255,255,255,0.5);
  text-decoration: none;
  transition: color 0.3s;
}

.footer-col ul li a:hover {
  color: var(--gold);
}

.contact-items {
  display: flex;
  flex-direction: column;
  gap: 16px;
}

.contact-item {
  display: flex;
  align-items: flex-start;
  gap: 12px;
  font-size: 14px;
  color: rgba(255,255,255,0.5);
}

.contact-item svg {
  width: 16px;
  height: 16px;
  flex-shrink: 0;
  margin-top: 2px;
  color: var(--gold);
}

.contact-item a {
  color: rgba(255,255,255,0.5);
  text-decoration: none;
  transition: color 0.3s;
}
.contact-item a:hover { color: var(--gold); }

.footer-bottom {
  border-top: 1px solid rgba(255,255,255,0.07);
  padding: 24px 0;
}

.footer-bottom .container {
  display: flex;
  justify-content: space-between;
  align-items: center;
  gap: 20px;
}

.footer-bottom p {
  font-size: 12px;
  color: rgba(255,255,255,0.3);
}

.footer-note {
  font-style: italic;
}

@media (max-width: 1024px) {
  .footer-grid {
    grid-template-columns: 1fr 1fr;
    gap: 40px;
  }
  .footer-brand { grid-column: 1 / -1; }
}

@media (max-width: 600px) {
  .footer-grid { grid-template-columns: 1fr; gap: 32px; }
  .footer-bottom .container { flex-direction: column; text-align: center; }
}
</style>
