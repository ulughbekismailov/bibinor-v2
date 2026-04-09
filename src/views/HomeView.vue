<template>
  <div class="home">

    <!-- HERO -->
    <section class="hero">
      <div class="hero-slides">
        <div
          v-for="(slide, i) in slides"
          :key="i"
          class="hero-slide"
          :class="{ active: currentSlide === i }"
          :style="{ backgroundImage: `url(${slide.img})` }"
        ></div>
      </div>
      <div class="hero-overlay"></div>
      <div class="hero-content container">
        <div class="hero-label">Veterinary Pharmaceuticals</div>
        <h1 class="hero-title">
          Здоровье животных —<br />
          <em>наш главный приоритет</em>
        </h1>
        <p class="hero-desc">
          Более 25 лет BIBINOR создаёт высококачественные ветеринарные препараты,<br />
          сертифицированные по международным стандартам GMP и Halal.
        </p>
        <div class="hero-actions">
          <RouterLink to="/products" class="btn-primary">Наши препараты</RouterLink>
          <RouterLink to="/about" class="btn-outline">О компании</RouterLink>
        </div>
      </div>
      <div class="slide-indicators">
        <button
          v-for="(s, i) in slides"
          :key="i"
          :class="{ active: currentSlide === i }"
          @click="currentSlide = i"
        ></button>
      </div>
      <div class="scroll-hint">
        <span>Прокрутите вниз</span>
        <div class="scroll-line"></div>
      </div>
    </section>

    <!-- STATS -->
    <section class="stats-bar">
      <div class="container">
        <div class="stats-grid">
          <div class="stat-item" v-for="s in stats" :key="s.label">
            <div class="stat-num">{{ s.num }}</div>
            <div class="stat-label">{{ s.label }}</div>
          </div>
        </div>
      </div>
    </section>

    <!-- ABOUT INTRO -->
    <section class="about-intro">
      <div class="container">
        <div class="about-grid">
          <div class="about-images">
            <div class="img-main">
              <img src="https://images.unsplash.com/photo-1628771065518-0d82f1938462?w=700&q=80" alt="Лаборатория" />
            </div>
            <div class="img-secondary">
              <img src="https://images.unsplash.com/photo-1516467508483-a7212febe31a?w=400&q=80" alt="Животные" />
              <div class="years-badge">
                <span class="years-num">25+</span>
                <span class="years-txt">лет<br/>опыта</span>
              </div>
            </div>
          </div>
          <div class="about-text">
            <div class="section-label">О компании</div>
            <h2 class="section-title">Лидер ветеринарной фармацевтики Узбекистана</h2>
            <p>Компания BIBINOR на протяжении более чем двух десятилетий занимает ведущие позиции на рынке ветеринарных препаратов Республики Узбекистан. Наше производство оснащено современным оборудованием и функционирует в строгом соответствии с международными стандартами качества.</p>
            <p style="margin-top: 16px;">Каждый препарат, выпускаемый под маркой BIBINOR, проходит многоступенчатый контроль качества и подтверждён необходимыми сертификатами, включая GMP, Halal и ISO.</p>
            <div class="advantages">
              <div class="adv-item" v-for="a in advantages" :key="a.title">
                <div class="adv-icon">{{ a.icon }}</div>
                <div>
                  <strong>{{ a.title }}</strong>
                  <p>{{ a.text }}</p>
                </div>
              </div>
            </div>
            <RouterLink to="/about" class="btn-primary" style="margin-top: 36px;">Подробнее о нас</RouterLink>
          </div>
        </div>
      </div>
    </section>

    <!-- PRODUCTS -->
    <section class="products-section">
      <div class="container">
        <div class="section-header">
          <div>
            <div class="section-label">Линейка продукции</div>
            <h2 class="section-title" style="color: var(--white)">Наши препараты</h2>
          </div>
          <RouterLink to="/products" class="btn-outline">Все препараты →</RouterLink>
        </div>
        <div class="products-grid">
          <RouterLink
            v-for="p in products"
            :key="p.id"
            :to="`/products/${p.id}`"
            class="product-card"
          >
            <div class="card-top" :style="{ background: p.color }">
              <div class="card-icon">{{ p.icon }}</div>
              <div class="card-category">{{ p.category }}</div>
              <div v-if="p.badge" class="card-badge">{{ p.badge }}</div>
            </div>
            <div class="card-body">
              <h3>{{ p.name }}</h3>
              <p>{{ p.subtitle }}</p>
              <div class="card-animals">
                <span v-for="a in p.animals.slice(0, 2)" :key="a">{{ a }}</span>
              </div>
              <div class="card-arrow">Подробнее →</div>
            </div>
          </RouterLink>
        </div>
      </div>
    </section>

    <!-- CERTS -->
    <section class="certs-section">
      <div class="container">
        <div class="certs-grid">
          <div class="certs-text">
            <div class="section-label">Качество и доверие</div>
            <h2 class="section-title">Международная сертификация</h2>
            <p>Производство BIBINOR сертифицировано по строжайшим международным стандартам, что подтверждает наш неизменно высокий уровень качества и безопасности продукции.</p>
            <RouterLink to="/certificates" class="btn-primary" style="margin-top: 32px;">Смотреть сертификаты</RouterLink>
          </div>
          <div class="certs-cards">
            <div class="cert-card" v-for="c in certs" :key="c.name">
              <div class="cert-icon">{{ c.icon }}</div>
              <div class="cert-name">{{ c.name }}</div>
              <div class="cert-desc">{{ c.desc }}</div>
            </div>
          </div>
        </div>
      </div>
    </section>

    <!-- ANIMALS SECTION -->
    <section class="animals-section">
      <div class="container">
        <div class="section-label" style="text-align:center">Сферы применения</div>
        <h2 class="section-title" style="text-align:center; margin-bottom: 60px">Для каких животных</h2>
        <div class="animals-grid">
          <div class="animal-card" v-for="a in animalTypes" :key="a.name">
            <div class="animal-img">
              <img :src="a.img" :alt="a.name" />
            </div>
            <div class="animal-info">
              <div class="animal-icon">{{ a.icon }}</div>
              <h3>{{ a.name }}</h3>
              <p>{{ a.count }} препаратов</p>
            </div>
          </div>
        </div>
      </div>
    </section>

    <!-- CTA -->
    <section class="cta-section">
      <div class="cta-bg"></div>
      <div class="container">
        <div class="cta-content">
          <div class="section-label" style="color: var(--gold)">Свяжитесь с нами</div>
          <h2 style="color: var(--white); font-size: clamp(30px,4vw,52px)">Готовы к сотрудничеству?</h2>
          <p>Наши специалисты проконсультируют вас по любым вопросам применения препаратов и условиям дистрибуции.</p>
          <div class="cta-actions">
            <RouterLink to="/contact" class="btn-primary">Написать нам</RouterLink>
            <a href="tel:+998995203040" class="btn-outline">+998 99 520 30 40</a>
          </div>
        </div>
      </div>
    </section>

  </div>
</template>

<script setup>
import { ref, onMounted, onUnmounted } from 'vue'
import { products } from '../data/products.js'

const slides = [
  { img: 'https://avatars.mds.yandex.net/i?id=a4c3b47662460f722dea296cc9319fd5_l-5304692-images-thumbs&ref=rim&n=13&w=1500&h=597' },
  { img: 'https://i.ytimg.com/vi/Gymfy2HIRyM/maxresdefault.jpg?sqp=-oaymwEmCIAKENAF8quKqQMa8AEB-AH-CYAC0AWKAgwIABABGDUgVShyMA8=&amp;rs=AOn4CLDNKbWYqR3JqIoMyFNZZp5ibj7N6w' },
  { img: 'https://popugaychiki.com/wp-content/uploads/2020/09/vet2.jpg' },
]

const currentSlide = ref(0)
let slideTimer = null

onMounted(() => {
  slideTimer = setInterval(() => {
    currentSlide.value = (currentSlide.value + 1) % slides.length
  }, 5000)
})

onUnmounted(() => clearInterval(slideTimer))

const stats = [
  { num: '25+', label: 'Лет на рынке' },
  { num: '5', label: 'Уникальных препаратов' },
  { num: 'GMP', label: 'Сертификат качества' },
  { num: 'Halal', label: 'Сертифицировано' },
  { num: '100%', label: 'Местное производство' },
]

const advantages = [
  { icon: '🏭', title: 'Собственное производство', text: 'Полный цикл производства на современном заводе' },
  { icon: '🔬', title: 'Научная база', text: 'Препараты разработаны ведущими специалистами' },
  { icon: '✅', title: 'Государственная регистрация', text: 'Все препараты прошли официальную регистрацию' },
]

const certs = [
  { icon: '🏆', name: 'GMP', desc: 'Международный стандарт надлежащей производственной практики' },
  { icon: '☪️', name: 'HALAL', desc: 'Сертификат соответствия исламским стандартам качества' },
  { icon: '📋', name: 'ISO', desc: 'Международный стандарт системы менеджмента качества' },
]

const animalTypes = [
  { name: 'Крупный рогатый скот', icon: '🐄', count: 5, img: 'https://images.unsplash.com/photo-1500595046743-cd271d694d30?w=500&q=80' },
  { name: 'Овцы и козы', icon: '🐑', count: 4, img: 'https://images.unsplash.com/photo-1548199973-03cce0bbc87b?w=500&q=80' },
  { name: 'Птицеводство', icon: '🐔', count: 3, img: 'https://images.unsplash.com/photo-1548550023-2bdb3c5beed7?w=500&q=80' },
  { name: 'Домашние животные', icon: '🐕', count: 2, img: 'https://images.unsplash.com/photo-1518717758536-85ae29035b6d?w=500&q=80' },
]
</script>

<style scoped>
/* HERO */
.hero {
  position: relative;
  height: 100vh;
  min-height: 700px;
  display: flex;
  align-items: center;
  overflow: hidden;
}

.hero-slides { position: absolute; inset: 0; }

.hero-slide {
  position: absolute;
  inset: 0;
  background-size: cover;
  background-position: center;
  opacity: 0;
  transition: opacity 1.2s ease;
  transform: scale(1.05);
}

.hero-slide.active {
  opacity: 1;
  transform: scale(1);
  transition: opacity 1.2s ease, transform 6s ease;
}

.hero-overlay {
  position: absolute;
  inset: 0;
  background: linear-gradient(
    135deg,
    rgba(11,29,53,0.88) 0%,
    rgba(11,29,53,0.6) 60%,
    rgba(11,29,53,0.4) 100%
  );
}

.hero-content {
  position: relative;
  z-index: 2;
}

.hero-label {
  font-size: 11px;
  font-weight: 600;
  letter-spacing: 5px;
  text-transform: uppercase;
  color: var(--gold);
  margin-bottom: 24px;
  display: flex;
  align-items: center;
  gap: 16px;
}

.hero-label::before {
  content: '';
  display: block;
  width: 40px;
  height: 1px;
  background: var(--gold);
}

.hero-title {
  font-size: clamp(40px, 6vw, 80px);
  color: var(--white);
  font-weight: 300;
  line-height: 1.1;
  margin-bottom: 28px;
}

.hero-title em {
  font-style: italic;
  color: var(--gold);
}

.hero-desc {
  font-size: 16px;
  color: rgba(255,255,255,0.7);
  line-height: 1.8;
  max-width: 580px;
  margin-bottom: 44px;
}

.hero-actions {
  display: flex;
  gap: 16px;
  flex-wrap: wrap;
}

.slide-indicators {
  position: absolute;
  bottom: 40px;
  left: 50%;
  transform: translateX(-50%);
  display: flex;
  gap: 10px;
  z-index: 3;
}

.slide-indicators button {
  width: 32px;
  height: 2px;
  background: rgba(255,255,255,0.3);
  border: none;
  cursor: pointer;
  transition: all 0.3s;
}

.slide-indicators button.active {
  background: var(--gold);
  width: 48px;
}

.scroll-hint {
  position: absolute;
  right: 40px;
  bottom: 40px;
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 12px;
  z-index: 3;
}

.scroll-hint span {
  font-size: 10px;
  letter-spacing: 3px;
  text-transform: uppercase;
  color: rgba(255,255,255,0.4);
  writing-mode: vertical-rl;
}

.scroll-line {
  width: 1px;
  height: 60px;
  background: linear-gradient(to bottom, rgba(255,255,255,0.3), transparent);
  animation: scrollAnim 2s ease infinite;
}

@keyframes scrollAnim {
  0% { transform: scaleY(0); transform-origin: top; }
  50% { transform: scaleY(1); transform-origin: top; }
  51% { transform: scaleY(1); transform-origin: bottom; }
  100% { transform: scaleY(0); transform-origin: bottom; }
}

/* STATS */
.stats-bar {
  background: var(--navy);
  padding: 0;
}

.stats-grid {
  display: grid;
  grid-template-columns: repeat(5, 1fr);
  border-top: 1px solid rgba(255,255,255,0.07);
}

.stat-item {
  padding: 36px 28px;
  border-right: 1px solid rgba(255,255,255,0.07);
  text-align: center;
}

.stat-item:last-child { border-right: none; }

.stat-num {
  font-family: 'Cormorant Garamond', serif;
  font-size: 36px;
  font-weight: 600;
  color: var(--gold);
  line-height: 1;
  margin-bottom: 8px;
}

.stat-label {
  font-size: 11px;
  font-weight: 500;
  letter-spacing: 2px;
  text-transform: uppercase;
  color: rgba(255,255,255,0.4);
}

/* ABOUT */
.about-intro {
  padding: 120px 0;
}

.about-grid {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 80px;
  align-items: center;
}

.about-images {
  position: relative;
}

.img-main img {
  width: 100%;
  height: 500px;
  object-fit: cover;
}

.img-secondary {
  position: absolute;
  bottom: -40px;
  right: -40px;
  width: 220px;
}

.img-secondary img {
  width: 100%;
  height: 180px;
  object-fit: cover;
  border: 4px solid var(--white);
}

.years-badge {
  position: absolute;
  top: -20px;
  left: -20px;
  background: var(--gold);
  width: 90px;
  height: 90px;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  text-align: center;
}

.years-num {
  font-family: 'Cormorant Garamond', serif;
  font-size: 28px;
  font-weight: 700;
  color: var(--navy);
  line-height: 1;
}

.years-txt {
  font-size: 10px;
  font-weight: 600;
  letter-spacing: 1px;
  color: var(--navy);
  text-transform: uppercase;
  line-height: 1.4;
}

.about-text p { font-size: 15px; line-height: 1.8; color: var(--text-body); }

.advantages {
  margin-top: 36px;
  display: flex;
  flex-direction: column;
  gap: 20px;
}

.adv-item {
  display: flex;
  gap: 16px;
  align-items: flex-start;
}

.adv-icon {
  font-size: 22px;
  flex-shrink: 0;
  margin-top: 2px;
}

.adv-item strong {
  font-family: 'Cormorant Garamond', serif;
  font-size: 17px;
  color: var(--navy);
  display: block;
  margin-bottom: 4px;
}

.adv-item p {
  font-size: 13px;
  color: var(--gray);
  margin: 0;
}

/* PRODUCTS */
.products-section {
  background: var(--navy);
  padding: 100px 0;
}

.section-header {
  display: flex;
  justify-content: space-between;
  align-items: flex-end;
  margin-bottom: 56px;
  gap: 20px;
}

.products-grid {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 2px;
}

.product-card {
  background: var(--navy-light);
  text-decoration: none;
  transition: transform 0.3s ease, box-shadow 0.3s ease;
  display: flex;
  flex-direction: column;
  overflow: hidden;
}

.product-card:hover {
  transform: translateY(-6px);
  box-shadow: 0 20px 60px rgba(0,0,0,0.4);
  z-index: 1;
}

.card-top {
  padding: 36px 28px 28px;
  position: relative;
  min-height: 140px;
  display: flex;
  flex-direction: column;
  justify-content: flex-end;
}

.card-icon {
  font-size: 32px;
  margin-bottom: 12px;
}

.card-category {
  font-size: 10px;
  font-weight: 600;
  letter-spacing: 3px;
  text-transform: uppercase;
  color: rgba(255,255,255,0.5);
}

.card-badge {
  position: absolute;
  top: 16px;
  right: 16px;
  background: var(--gold);
  color: var(--navy);
  font-size: 9px;
  font-weight: 700;
  letter-spacing: 1px;
  padding: 5px 10px;
  text-transform: uppercase;
}

.card-body {
  padding: 28px;
  flex: 1;
  display: flex;
  flex-direction: column;
}

.card-body h3 {
  font-size: 22px;
  color: var(--white);
  margin-bottom: 10px;
  font-family: 'Cormorant Garamond', serif;
  font-weight: 700;
  letter-spacing: 1px;
}

.card-body p {
  font-size: 13px;
  color: rgba(255,255,255,0.5);
  line-height: 1.6;
  flex: 1;
}

.card-animals {
  display: flex;
  gap: 8px;
  flex-wrap: wrap;
  margin-top: 16px;
}

.card-animals span {
  font-size: 10px;
  font-weight: 500;
  letter-spacing: 1px;
  color: rgba(255,255,255,0.4);
  border: 1px solid rgba(255,255,255,0.1);
  padding: 4px 10px;
}

.card-arrow {
  margin-top: 20px;
  font-size: 12px;
  font-weight: 600;
  letter-spacing: 2px;
  text-transform: uppercase;
  color: var(--gold);
  transition: gap 0.3s;
}

/* CERTS */
.certs-section {
  padding: 100px 0;
  background: var(--off-white);
}

.certs-grid {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 80px;
  align-items: center;
}

.certs-text p {
  font-size: 15px;
  line-height: 1.8;
  color: var(--text-body);
  margin-top: 20px;
}

.certs-cards {
  display: grid;
  grid-template-columns: 1fr;
  gap: 2px;
}

.cert-card {
  background: var(--white);
  padding: 32px 36px;
  display: flex;
  align-items: center;
  gap: 24px;
  border-left: 3px solid var(--gold);
  transition: transform 0.3s;
}

.cert-card:hover { transform: translateX(6px); }

.cert-icon { font-size: 28px; }

.cert-name {
  font-family: 'Cormorant Garamond', serif;
  font-size: 22px;
  font-weight: 700;
  color: var(--navy);
  margin-bottom: 4px;
  letter-spacing: 2px;
}

.cert-desc {
  font-size: 13px;
  color: var(--gray);
  line-height: 1.5;
}

/* ANIMALS */
.animals-section {
  padding: 100px 0;
}

.animals-grid {
  display: grid;
  grid-template-columns: repeat(4, 1fr);
  gap: 24px;
}

.animal-card {
  position: relative;
  overflow: hidden;
  cursor: default;
}

.animal-img img {
  width: 100%;
  height: 280px;
  object-fit: cover;
  transition: transform 0.5s ease;
}

.animal-card:hover .animal-img img {
  transform: scale(1.08);
}

.animal-info {
  position: absolute;
  bottom: 0;
  left: 0;
  right: 0;
  background: linear-gradient(to top, rgba(11,29,53,0.95) 0%, transparent 100%);
  padding: 36px 24px 24px;
  text-align: center;
}

.animal-icon { font-size: 28px; margin-bottom: 8px; }

.animal-info h3 {
  font-family: 'Cormorant Garamond', serif;
  font-size: 20px;
  color: var(--white);
  margin-bottom: 4px;
}

.animal-info p {
  font-size: 11px;
  color: var(--gold);
  letter-spacing: 2px;
  text-transform: uppercase;
}

/* CTA */
.cta-section {
  position: relative;
  background: var(--navy);
  padding: 100px 0;
  text-align: center;
  overflow: hidden;
}

.cta-bg {
  position: absolute;
  inset: 0;
  background: radial-gradient(ellipse at center, rgba(201,168,76,0.08) 0%, transparent 70%);
}

.cta-content {
  position: relative;
  z-index: 1;
}

.cta-content p {
  font-size: 16px;
  color: rgba(255,255,255,0.6);
  max-width: 520px;
  margin: 20px auto 0;
  line-height: 1.8;
}

.cta-actions {
  display: flex;
  gap: 16px;
  justify-content: center;
  margin-top: 44px;
  flex-wrap: wrap;
}

/* RESPONSIVE */
@media (max-width: 1024px) {
  .about-grid { grid-template-columns: 1fr; }
  .about-images { margin-bottom: 60px; }
  .img-secondary { right: 0; }
  .products-grid { grid-template-columns: 1fr 1fr; }
  .certs-grid { grid-template-columns: 1fr; }
  .animals-grid { grid-template-columns: 1fr 1fr; }
  .stats-grid { grid-template-columns: repeat(3, 1fr); }
}

@media (max-width: 768px) {
  .products-grid { grid-template-columns: 1fr; }
  .animals-grid { grid-template-columns: 1fr 1fr; }
  .stats-grid { grid-template-columns: 1fr 1fr; }
  .section-header { flex-direction: column; align-items: flex-start; }
  .hero-desc { display: none; }
}

@media (max-width: 480px) {
  .animals-grid { grid-template-columns: 1fr; }
  .stats-grid { grid-template-columns: 1fr 1fr; }
}
</style>
