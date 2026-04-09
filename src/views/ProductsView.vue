<template>
  <div class="products-page">

    <section class="page-hero">
      <div class="hero-bg" style="background-image: url('https://storage.myseldon.com/news-pict-d0/D04F1DAC909A2D318C17C61A81E6FB78')"></div>
      <div class="hero-overlay"></div>
      <div class="container">
        <div class="page-hero-content">
          <div class="breadcrumb">
            <RouterLink to="/">Главная</RouterLink>
            <span>/</span>
            <span>Препараты</span>
          </div>
          <h1>Линейка препаратов</h1>
          <p>5 уникальных препаратов для комплексной заботы о здоровье животных</p>
        </div>
      </div>
    </section>

    <!-- FILTER -->
    <section class="filter-bar">
      <div class="container">
        <div class="filter-buttons">
          <button
            v-for="cat in categories"
            :key="cat"
            :class="['filter-btn', { active: activeCategory === cat }]"
            @click="activeCategory = cat"
          >{{ cat }}</button>
        </div>
      </div>
    </section>

    <!-- PRODUCTS LIST -->
    <section class="products-list">
      <div class="container">
        <TransitionGroup name="list" tag="div" class="prods-grid">
          <div
            v-for="p in filteredProducts"
            :key="p.id"
            class="prod-card"
          >
            <div class="prod-card-image">
              <img :src="p.image" :alt="p.name" />
              <div class="prod-overlay">
                <RouterLink :to="`/products/${p.id}`" class="btn-primary">Подробнее</RouterLink>
              </div>
            </div>
            <div class="prod-card-body">
              <div class="prod-meta">
                <span class="prod-category">{{ p.category }}</span>
                <span v-if="p.badge" class="prod-badge">{{ p.badge }}</span>
              </div>
              <h2>{{ p.name }}</h2>
              <p class="prod-subtitle">{{ p.subtitle }}</p>
              <p class="prod-desc">{{ p.description }}</p>
              <div class="prod-animals">
                <span class="anim-label">Применяется для:</span>
                <div class="anim-tags">
                  <span v-for="a in p.animals" :key="a">{{ a }}</span>
                </div>
              </div>
              <RouterLink :to="`/products/${p.id}`" class="prod-link">
                Полная информация
                <svg width="14" height="14" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><path d="M5 12h14M12 5l7 7-7 7"/></svg>
              </RouterLink>
            </div>
          </div>
        </TransitionGroup>
      </div>
    </section>

    <!-- DISCLAIMER -->
    <section class="disclaimer">
      <div class="container">
        <div class="disclaimer-box">
          <div class="disc-icon">⚠️</div>
          <div>
            <strong>Важное примечание</strong>
            <p>Все препараты BIBINOR являются ветеринарными лекарственными средствами. Применение осуществляется строго по назначению и под контролем квалифицированного ветеринарного врача. Перед применением внимательно ознакомьтесь с инструкцией.</p>
          </div>
        </div>
      </div>
    </section>

  </div>
</template>

<script setup>
import { ref, computed } from 'vue'
import { products, categories } from '../data/products.js'

const activeCategory = ref('Все препараты')

const filteredProducts = computed(() => {
  if (activeCategory.value === 'Все препараты') return products
  return products.filter(p => p.category === activeCategory.value)
})
</script>

<style scoped>
.page-hero {
  position: relative;
  height: 380px;
  display: flex;
  align-items: flex-end;
  padding-bottom: 60px;
  overflow: hidden;
}
.hero-bg { position: absolute; inset: 0; background-size: cover; background-position: center; }
.hero-overlay { position: absolute; inset: 0; background: linear-gradient(to right, rgba(11,29,53,0.92) 0%, rgba(11,29,53,0.55) 100%); }
.page-hero-content { position: relative; z-index: 1; }
.breadcrumb { display: flex; gap: 10px; align-items: center; margin-bottom: 16px; font-size: 12px; color: rgba(255,255,255,0.5); }
.breadcrumb a { color: var(--gold); text-decoration: none; }
.page-hero-content h1 { font-size: clamp(32px, 5vw, 56px); color: var(--white); margin-bottom: 12px; }
.page-hero-content p { font-size: 16px; color: rgba(255,255,255,0.6); }

/* FILTER */
.filter-bar {
  background: var(--navy);
  padding: 0;
  border-bottom: 1px solid rgba(255,255,255,0.07);
}

.filter-buttons {
  display: flex;
  gap: 0;
  overflow-x: auto;
  scrollbar-width: none;
}

.filter-btn {
  font-family: 'Jost', sans-serif;
  font-size: 11px;
  font-weight: 600;
  letter-spacing: 2px;
  text-transform: uppercase;
  color: rgba(255,255,255,0.5);
  background: none;
  border: none;
  border-bottom: 2px solid transparent;
  padding: 20px 28px;
  cursor: pointer;
  transition: all 0.3s;
  white-space: nowrap;
}

.filter-btn:hover { color: var(--white); }
.filter-btn.active { color: var(--gold); border-bottom-color: var(--gold); }

/* PRODUCTS */
.products-list { padding: 80px 0; }

.prods-grid {
  display: flex;
  flex-direction: column;
  gap: 2px;
}

.prod-card {
  display: grid;
  grid-template-columns: 400px 1fr;
  background: var(--off-white);
  overflow: hidden;
  transition: box-shadow 0.3s;
}

.prod-card:hover {
  box-shadow: 0 8px 40px rgba(11,29,53,0.12);
}

.prod-card:nth-child(even) {
  grid-template-columns: 1fr 400px;
}

.prod-card:nth-child(even) .prod-card-image {
  order: 2;
}

.prod-card-image {
  position: relative;
  overflow: hidden;
}

.prod-card-image img {
  width: 100%;
  height: 100%;
  min-height: 340px;
  object-fit: cover;
  transition: transform 0.5s ease;
}

.prod-card:hover .prod-card-image img {
  transform: scale(1.05);
}

.prod-overlay {
  position: absolute;
  inset: 0;
  background: rgba(11,29,53,0.6);
  display: flex;
  align-items: center;
  justify-content: center;
  opacity: 0;
  transition: opacity 0.3s;
}

.prod-card:hover .prod-overlay { opacity: 1; }

.prod-card-body {
  padding: 48px 52px;
  display: flex;
  flex-direction: column;
  justify-content: center;
}

.prod-meta {
  display: flex;
  gap: 12px;
  align-items: center;
  margin-bottom: 16px;
}

.prod-category {
  font-size: 10px;
  font-weight: 600;
  letter-spacing: 3px;
  text-transform: uppercase;
  color: var(--gold);
}

.prod-badge {
  font-size: 10px;
  font-weight: 700;
  color: var(--navy);
  background: var(--gold);
  padding: 3px 10px;
  letter-spacing: 1px;
}

.prod-card-body h2 {
  font-size: 38px;
  color: var(--navy);
  margin-bottom: 8px;
  letter-spacing: 2px;
}

.prod-subtitle {
  font-size: 14px;
  color: var(--gold);
  font-weight: 500;
  margin-bottom: 20px;
  letter-spacing: 1px;
}

.prod-desc {
  font-size: 14px;
  color: var(--text-body);
  line-height: 1.8;
  margin-bottom: 28px;
}

.prod-animals { margin-bottom: 28px; }

.anim-label {
  font-size: 10px;
  font-weight: 600;
  letter-spacing: 2px;
  text-transform: uppercase;
  color: var(--gray);
  display: block;
  margin-bottom: 10px;
}

.anim-tags {
  display: flex;
  flex-wrap: wrap;
  gap: 8px;
}

.anim-tags span {
  font-size: 11px;
  color: var(--navy);
  border: 1px solid rgba(11,29,53,0.2);
  padding: 4px 12px;
}

.prod-link {
  display: inline-flex;
  align-items: center;
  gap: 10px;
  font-size: 12px;
  font-weight: 600;
  letter-spacing: 2px;
  text-transform: uppercase;
  color: var(--navy);
  text-decoration: none;
  border-bottom: 1px solid var(--navy);
  padding-bottom: 4px;
  width: fit-content;
  transition: color 0.3s, border-color 0.3s;
}

.prod-link:hover { color: var(--gold); border-color: var(--gold); }

/* DISCLAIMER */
.disclaimer { background: var(--off-white); padding: 40px 0; }

.disclaimer-box {
  display: flex;
  gap: 20px;
  align-items: flex-start;
  background: var(--white);
  padding: 28px 32px;
  border-left: 3px solid var(--gold);
}

.disc-icon { font-size: 24px; flex-shrink: 0; }

.disclaimer-box strong {
  font-size: 14px;
  color: var(--navy);
  display: block;
  margin-bottom: 8px;
  letter-spacing: 1px;
}

.disclaimer-box p { font-size: 13px; color: var(--text-body); line-height: 1.7; }

/* TRANSITION */
.list-enter-active, .list-leave-active { transition: all 0.3s ease; }
.list-enter-from, .list-leave-to { opacity: 0; transform: translateY(10px); }

@media (max-width: 900px) {
  .prod-card,
  .prod-card:nth-child(even) {
    grid-template-columns: 1fr;
  }
  .prod-card:nth-child(even) .prod-card-image { order: 0; }
  .prod-card-body { padding: 32px; }
  .prod-card-image img { min-height: 240px; }
}
</style>
