<template>
  <div class="certs-page">

    <section class="page-hero">
      <div class="hero-bg" style="background-image: url('https://images.unsplash.com/photo-1582719188393-bb71ca45dbb9?w=1400&q=80')"></div>
      <div class="hero-overlay"></div>
      <div class="container">
        <div class="page-hero-content">
          <div class="breadcrumb">
            <RouterLink to="/">Главная</RouterLink><span>/</span><span>Сертификаты</span>
          </div>
          <h1>Сертификаты и документы</h1>
          <p>Наше производство подтверждено международными стандартами качества</p>
        </div>
      </div>
    </section>

    <section class="certs-intro">
      <div class="container">
        <div class="intro-text">
          <div class="section-label">Качество</div>
          <h2 class="section-title">Международное признание</h2>
          <p>Компания BIBINOR придаёт первостепенное значение качеству выпускаемой продукции. Наше производство прошло аудит и сертификацию по строжайшим международным стандартам, что является гарантией безопасности и эффективности каждого препарата.</p>
        </div>
      </div>
    </section>

    <section class="certs-main">
      <div class="container">
        <div class="certs-grid">
          <div class="cert-card-large" v-for="cert in certs" :key="cert.name">
            <div class="cert-card-left" :style="{ background: cert.color }">
              <div class="cert-emblem">{{ cert.emblem }}</div>
              <div class="cert-name-large">{{ cert.name }}</div>
            </div>
            <div class="cert-card-right">
              <div class="section-label">{{ cert.label }}</div>
              <h3>{{ cert.title }}</h3>
              <p>{{ cert.description }}</p>
              <ul class="cert-points">
                <li v-for="p in cert.points" :key="p">
                  <span>✓</span> {{ p }}
                </li>
              </ul>
            </div>
          </div>
        </div>
      </div>
    </section>

    <section class="standards-section">
      <div class="container">
        <div class="section-label" style="text-align:center">Стандарты производства</div>
        <h2 class="section-title" style="text-align:center; color: var(--white); margin-bottom: 56px">Наши гарантии качества</h2>
        <div class="standards-grid">
          <div class="std-item" v-for="s in standards" :key="s.title">
            <div class="std-number">{{ s.num }}</div>
            <h3>{{ s.title }}</h3>
            <p>{{ s.text }}</p>
          </div>
        </div>
      </div>
    </section>

    <section class="contact-cta">
      <div class="container">
        <div class="cta-box">
          <h2>Нужны официальные документы?</h2>
          <p>По запросу мы предоставляем копии всех сертификатов и регистрационных документов для официальных целей.</p>
          <RouterLink to="/contact" class="btn-primary">Запросить документы</RouterLink>
        </div>
      </div>
    </section>

  </div>
</template>

<script setup>
const certs = [
  {
    name: 'GMP',
    emblem: '🏆',
    label: 'Производственный стандарт',
    title: 'Good Manufacturing Practice — Надлежащая производственная практика',
    color: 'var(--navy)',
    description: 'Сертификат GMP (Good Manufacturing Practice) — международный стандарт, регулирующий все аспекты производства фармацевтических препаратов. Его получение свидетельствует о том, что производство BIBINOR организовано в соответствии с наивысшими требованиями к качеству, чистоте и безопасности.',
    points: [
      'Строгий контроль всего производственного процесса',
      'Валидация производственного оборудования',
      'Документирование каждой производственной серии',
      'Регулярные внутренние и внешние аудиты',
      'Надлежащие условия хранения и транспортировки',
    ]
  },
  {
    name: 'HALAL',
    emblem: '☪️',
    label: 'Исламский стандарт',
    title: 'Halal — Соответствие исламским требованиям',
    color: '#1a4a2a',
    description: 'Сертификат Halal подтверждает, что производство препаратов BIBINOR полностью соответствует требованиям исламского права. Это означает, что при производстве не используются запрещённые компоненты, а весь процесс отвечает этическим нормам.',
    points: [
      'Отсутствие запрещённых компонентов (харам)',
      'Сертифицированное сырьё и вспомогательные вещества',
      'Регулярный контроль со стороны сертифицирующего органа',
      'Соответствие требованиям для экспорта в исламские страны',
      'Этичное и гуманное производство',
    ]
  },
  {
    name: 'ISO',
    emblem: '📋',
    label: 'Системный стандарт',
    title: 'ISO — Международная стандартизация системы менеджмента',
    color: '#1a2a4a',
    description: 'Сертификат ISO подтверждает, что система менеджмента качества компании BIBINOR соответствует международным стандартам ISO. Это означает, что все процессы — от закупки сырья до поставки готовой продукции — организованы системно и эффективно.',
    points: [
      'Документированная система менеджмента качества',
      'Постоянное совершенствование процессов',
      'Ориентация на удовлетворённость потребителей',
      'Управление рисками и возможностями',
      'Международное признание и доверие',
    ]
  },
]

const standards = [
  { num: '01', title: 'Входной контроль', text: 'Каждая партия сырья проходит обязательный лабораторный анализ перед запуском в производство.' },
  { num: '02', title: 'Производственный контроль', text: 'Непрерывный мониторинг всех параметров производственного процесса на каждом этапе.' },
  { num: '03', title: 'Контроль готовой продукции', text: 'Каждая серия готовых препаратов проходит полный аналитический контроль перед выпуском.' },
  { num: '04', title: 'Хранение и логистика', text: 'Соблюдение необходимых условий хранения и транспортировки, гарантирующих сохранность препаратов.' },
]
</script>

<style scoped>
.page-hero { position: relative; height: 380px; display: flex; align-items: flex-end; padding-bottom: 60px; overflow: hidden; }
.hero-bg { position: absolute; inset: 0; background-size: cover; background-position: center; }
.hero-overlay { position: absolute; inset: 0; background: linear-gradient(to right, rgba(11,29,53,0.92) 0%, rgba(11,29,53,0.55) 100%); }
.page-hero-content { position: relative; z-index: 1; }
.breadcrumb { display: flex; gap: 10px; align-items: center; margin-bottom: 16px; font-size: 12px; color: rgba(255,255,255,0.5); }
.breadcrumb a { color: var(--gold); text-decoration: none; }
.page-hero-content h1 { font-size: clamp(32px, 5vw, 56px); color: var(--white); margin-bottom: 12px; }
.page-hero-content p { font-size: 16px; color: rgba(255,255,255,0.6); }

.certs-intro { padding: 80px 0; }
.intro-text { max-width: 700px; }
.intro-text p { font-size: 15px; line-height: 1.9; color: var(--text-body); margin-top: 20px; }

.certs-main { padding: 0 0 80px; }
.certs-grid { display: flex; flex-direction: column; gap: 2px; }

.cert-card-large {
  display: grid;
  grid-template-columns: 240px 1fr;
  background: var(--off-white);
  overflow: hidden;
  transition: box-shadow 0.3s;
}

.cert-card-large:hover { box-shadow: 0 8px 40px rgba(11,29,53,0.1); }

.cert-card-left {
  padding: 48px 36px;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  text-align: center;
}

.cert-emblem { font-size: 48px; margin-bottom: 20px; }

.cert-name-large {
  font-family: 'Cormorant Garamond', serif;
  font-size: 36px;
  font-weight: 700;
  color: var(--white);
  letter-spacing: 4px;
}

.cert-card-right { padding: 48px 52px; }

.cert-card-right h3 {
  font-size: 20px;
  color: var(--navy);
  margin-bottom: 16px;
  margin-top: 8px;
  line-height: 1.3;
}

.cert-card-right p { font-size: 14px; color: var(--text-body); line-height: 1.8; margin-bottom: 24px; }

.cert-points { list-style: none; display: flex; flex-direction: column; gap: 10px; }

.cert-points li {
  display: flex;
  gap: 12px;
  font-size: 13px;
  color: var(--text-body);
  align-items: flex-start;
}

.cert-points li span { color: var(--gold); font-weight: 700; flex-shrink: 0; }

.standards-section { background: var(--navy); padding: 80px 0; }

.standards-grid {
  display: grid;
  grid-template-columns: repeat(4, 1fr);
  gap: 2px;
}

.std-item {
  background: rgba(255,255,255,0.04);
  padding: 36px 32px;
  border-bottom: 2px solid transparent;
  transition: border-color 0.3s, background 0.3s;
}

.std-item:hover {
  background: rgba(255,255,255,0.07);
  border-bottom-color: var(--gold);
}

.std-number {
  font-family: 'Cormorant Garamond', serif;
  font-size: 48px;
  font-weight: 700;
  color: rgba(201,168,76,0.2);
  line-height: 1;
  margin-bottom: 16px;
}

.std-item h3 {
  font-size: 16px;
  color: var(--white);
  margin-bottom: 12px;
}

.std-item p { font-size: 13px; color: rgba(255,255,255,0.45); line-height: 1.7; }

.contact-cta { padding: 80px 0; }

.cta-box {
  background: var(--off-white);
  padding: 60px;
  text-align: center;
  border-top: 3px solid var(--gold);
}

.cta-box h2 { font-size: 32px; color: var(--navy); margin-bottom: 16px; }
.cta-box p { font-size: 15px; color: var(--text-body); max-width: 500px; margin: 0 auto 32px; line-height: 1.8; }

@media (max-width: 900px) {
  .cert-card-large { grid-template-columns: 1fr; }
  .cert-card-left { padding: 36px; }
  .cert-card-right { padding: 36px; }
  .standards-grid { grid-template-columns: 1fr 1fr; }
}
@media (max-width: 600px) {
  .standards-grid { grid-template-columns: 1fr; }
  .cta-box { padding: 36px 24px; }
}
</style>
