<template>
  <div class="product-detail" v-if="product">

    <!-- HERO -->
    <section class="detail-hero" :style="{ background: product.color }">
      <div class="detail-hero-img">
        <img :src="product.image" :alt="product.name" />
      </div>
      <div class="detail-hero-overlay"></div>
      <div class="container">
        <div class="detail-hero-content">
          <div class="breadcrumb">
            <RouterLink to="/">Главная</RouterLink>
            <span>/</span>
            <RouterLink to="/products">Препараты</RouterLink>
            <span>/</span>
            <span>{{ product.name }}</span>
          </div>
          <div class="prod-category-tag">{{ product.category }}</div>
          <h1>{{ product.name }}</h1>
          <p class="detail-subtitle">{{ product.subtitle }}</p>
          <div v-if="product.badge" class="detail-badge">{{ product.badge }}</div>
        </div>
      </div>
    </section>

    <!-- CONTENT -->
    <section class="detail-content">
      <div class="container">
        <div class="detail-grid">
          <!-- MAIN -->
          <div class="detail-main">
            <div class="section-label">Описание препарата</div>
            <h2 class="section-title">О препарате</h2>
            <div class="detail-text" v-html="formattedDescription"></div>

            <div style="margin-top: 56px">
              <div class="section-label">Показания</div>
              <h2 class="section-title">Показания к применению</h2>
              <ul class="indications-list">
                <li v-for="ind in product.indications" :key="ind">
                  <span class="ind-icon">✓</span>
                  {{ ind }}
                </li>
              </ul>
            </div>
          </div>

          <!-- SIDEBAR -->
          <div class="detail-sidebar">
            <div class="sidebar-card">
              <h3>Виды животных</h3>
              <div class="animal-list">
                <div class="animal-item" v-for="a in product.animals" :key="a">
                  <span class="animal-dot"></span>
                  {{ a }}
                </div>
              </div>
            </div>

            <div class="sidebar-card contact-card">
              <div class="contact-icon">💬</div>
              <h3>Нужна консультация?</h3>
              <p>Наши ветеринарные специалисты готовы ответить на ваши вопросы о применении препарата.</p>
              <RouterLink to="/contact" class="btn-primary" style="margin-top: 20px; width: 100%; justify-content: center;">Связаться</RouterLink>
              <a href="tel:+998995203040" style="display:block; text-align:center; margin-top: 12px; font-size: 13px; color: var(--gold); text-decoration: none; font-weight: 600;">+998 99 520 30 40</a>
            </div>

            <div class="sidebar-card cert-sidebar">
              <h3>Сертификаты</h3>
              <div class="cert-badges">
                <div class="cs-badge">GMP</div>
                <div class="cs-badge">HALAL</div>
                <div class="cs-badge">ISO</div>
              </div>
              <p>Препарат произведён в соответствии с международными стандартами качества.</p>
            </div>
          </div>
        </div>

        <!-- OTHER PRODUCTS -->
        <div class="other-products">
          <div class="section-label">Другие препараты</div>
          <h2 class="section-title" style="margin-bottom: 40px">Смотрите также</h2>
          <div class="other-grid">
            <RouterLink
              v-for="p in otherProducts"
              :key="p.id"
              :to="`/products/${p.id}`"
              class="other-card"
            >
              <div class="other-top" :style="{ background: p.color }">
                <div class="other-icon">{{ p.icon }}</div>
              </div>
              <div class="other-body">
                <h3>{{ p.name }}</h3>
                <p>{{ p.subtitle }}</p>
                <span class="other-link">Подробнее →</span>
              </div>
            </RouterLink>
          </div>
        </div>
      </div>
    </section>

  </div>

  <div v-else class="not-found">
    <div class="container">
      <h2>Препарат не найден</h2>
      <RouterLink to="/products" class="btn-primary" style="margin-top: 24px;">← Назад к препаратам</RouterLink>
    </div>
  </div>
</template>

<script setup>
import { computed } from 'vue'
import { useRoute } from 'vue-router'
import { products } from '../data/products.js'

const route = useRoute()

const product = computed(() => products.find(p => p.id === route.params.id))

const formattedDescription = computed(() => {
  if (!product.value) return ''
  return product.value.fullDescription
    .split('\n\n')
    .map(p => `<p>${p}</p>`)
    .join('')
})

const otherProducts = computed(() => {
  if (!product.value) return []
  return products.filter(p => p.id !== product.value.id).slice(0, 3)
})
</script>

<style scoped>
.detail-hero {
  position: relative;
  min-height: 460px;
  display: flex;
  align-items: flex-end;
  padding-bottom: 60px;
  overflow: hidden;
}

.detail-hero-img {
  position: absolute;
  inset: 0;
}

.detail-hero-img img {
  width: 100%;
  height: 100%;
  object-fit: cover;
  opacity: 0.25;
}

.detail-hero-overlay {
  position: absolute;
  inset: 0;
  background: linear-gradient(to right, rgba(0,0,0,0.7) 0%, rgba(0,0,0,0.2) 100%);
}

.detail-hero-content {
  position: relative;
  z-index: 1;
}

.breadcrumb {
  display: flex;
  gap: 10px;
  align-items: center;
  margin-bottom: 20px;
  font-size: 12px;
  color: rgba(255,255,255,0.5);
}

.breadcrumb a { color: var(--gold); text-decoration: none; }

.prod-category-tag {
  font-size: 10px;
  font-weight: 600;
  letter-spacing: 4px;
  text-transform: uppercase;
  color: var(--gold);
  margin-bottom: 16px;
}

.detail-hero-content h1 {
  font-size: clamp(40px, 6vw, 72px);
  color: var(--white);
  letter-spacing: 3px;
  margin-bottom: 12px;
}

.detail-subtitle {
  font-size: 16px;
  color: rgba(255,255,255,0.6);
  max-width: 500px;
}

.detail-badge {
  display: inline-block;
  background: var(--gold);
  color: var(--navy);
  font-size: 11px;
  font-weight: 700;
  letter-spacing: 2px;
  padding: 6px 16px;
  margin-top: 16px;
}

/* CONTENT */
.detail-content { padding: 80px 0 100px; }

.detail-grid {
  display: grid;
  grid-template-columns: 1fr 340px;
  gap: 60px;
  margin-bottom: 80px;
}

.detail-text { margin-top: 20px; }

.detail-text :deep(p) {
  font-size: 15px;
  line-height: 1.9;
  color: var(--text-body);
  margin-bottom: 20px;
}

.indications-list {
  list-style: none;
  margin-top: 20px;
  display: flex;
  flex-direction: column;
  gap: 2px;
}

.indications-list li {
  display: flex;
  align-items: center;
  gap: 16px;
  background: var(--off-white);
  padding: 16px 20px;
  font-size: 14px;
  color: var(--text-body);
  transition: background 0.3s;
}

.indications-list li:hover { background: #ede9e1; }

.ind-icon {
  color: var(--gold);
  font-weight: 700;
  font-size: 16px;
  flex-shrink: 0;
}

/* SIDEBAR */
.sidebar-card {
  background: var(--off-white);
  padding: 32px;
  margin-bottom: 2px;
}

.sidebar-card h3 {
  font-size: 14px;
  font-weight: 600;
  letter-spacing: 2px;
  text-transform: uppercase;
  color: var(--navy);
  margin-bottom: 20px;
  padding-bottom: 16px;
  border-bottom: 1px solid rgba(11,29,53,0.1);
}

.animal-list {
  display: flex;
  flex-direction: column;
  gap: 12px;
}

.animal-item {
  display: flex;
  align-items: center;
  gap: 12px;
  font-size: 14px;
  color: var(--text-body);
}

.animal-dot {
  width: 6px;
  height: 6px;
  background: var(--gold);
  border-radius: 50%;
  flex-shrink: 0;
}

.contact-card {
  background: var(--navy);
  text-align: center;
}

.contact-card h3 {
  color: var(--white);
  border-color: rgba(255,255,255,0.1);
  text-align: center;
}

.contact-icon { font-size: 32px; margin-bottom: 16px; }

.contact-card p {
  font-size: 13px;
  color: rgba(255,255,255,0.5);
  line-height: 1.7;
}

.cert-sidebar p {
  font-size: 12px;
  color: var(--gray);
  line-height: 1.7;
}

.cert-badges {
  display: flex;
  gap: 8px;
  margin-bottom: 16px;
}

.cs-badge {
  font-size: 11px;
  font-weight: 700;
  letter-spacing: 2px;
  color: var(--gold);
  border: 1px solid rgba(201,168,76,0.3);
  padding: 6px 14px;
}

/* OTHER PRODUCTS */
.other-grid {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 2px;
}

.other-card {
  background: var(--off-white);
  text-decoration: none;
  transition: transform 0.3s;
  overflow: hidden;
}

.other-card:hover { transform: translateY(-4px); }

.other-top {
  padding: 28px;
  display: flex;
  align-items: center;
}

.other-icon { font-size: 32px; }

.other-body { padding: 24px 28px; }

.other-body h3 {
  font-size: 20px;
  color: var(--navy);
  margin-bottom: 8px;
  letter-spacing: 1px;
}

.other-body p {
  font-size: 12px;
  color: var(--gray);
  line-height: 1.6;
  margin-bottom: 16px;
}

.other-link {
  font-size: 11px;
  font-weight: 600;
  letter-spacing: 2px;
  text-transform: uppercase;
  color: var(--gold);
}

.not-found {
  min-height: 60vh;
  display: flex;
  align-items: center;
  padding: 100px 0;
  text-align: center;
}

@media (max-width: 900px) {
  .detail-grid { grid-template-columns: 1fr; }
  .other-grid { grid-template-columns: 1fr; }
}
</style>
