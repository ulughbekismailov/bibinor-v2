<template>
  <div class="about-page">

    <!-- PAGE HERO -->
    <section class="page-hero">
      <div class="hero-bg" style="background-image: url('https://avatars.mds.yandex.net/get-altay/14381528/2a000001946045a1cae6e4ffc1c15a08718f/orig')"></div>
      <div class="hero-overlay"></div>
      <div class="container">
        <div class="page-hero-content">
          <div class="breadcrumb">
            <RouterLink to="/">Главная</RouterLink>
            <span>/</span>
            <span>О компании</span>
          </div>
          <h1>О компании BIBINOR</h1>
          <p>Более 25 лет на страже здоровья животных</p>
        </div>
      </div>
    </section>

    <!-- MISSION -->
    <section class="mission-section">
      <div class="container">
        <div class="mission-grid">
          <div class="mission-text">
            <div class="section-label">Наша история</div>
            <h2 class="section-title">Путь длиной в четверть века</h2>
            <p>Компания BIBINOR была основана с одной чёткой целью — обеспечить животноводов Узбекистана высококачественными, доступными и эффективными ветеринарными препаратами собственного производства. За четверть века работы мы прошли путь от небольшой лаборатории до ведущего фармацевтического предприятия страны.</p>
            <p style="margin-top: 16px;">Сегодня наши препараты применяются в сотнях хозяйств по всей Республике Узбекистан. Ежегодно тысячи ветеринарных врачей доверяют продукции BIBINOR здоровье своих пациентов.</p>
            <p style="margin-top: 16px;">Мы гордимся тем, что вносим вклад в развитие сельского хозяйства страны и обеспечение продовольственной безопасности. Каждый наш препарат — это результат многолетней научной работы, клинических испытаний и неустанного контроля качества.</p>
          </div>
          <div class="mission-values">
            <div class="value-card" v-for="v in values" :key="v.title">
              <div class="value-icon">{{ v.icon }}</div>
              <h3>{{ v.title }}</h3>
              <p>{{ v.text }}</p>
            </div>
          </div>
        </div>
      </div>
    </section>

    <!-- TIMELINE -->
    <section class="timeline-section">
      <div class="container">
        <div class="section-label" style="text-align:center">Наш путь</div>
        <h2 class="section-title" style="text-align:center; margin-bottom: 64px">Ключевые этапы</h2>
        <div class="timeline">
          <div class="timeline-item" v-for="(item, i) in timeline" :key="i" :class="{ right: i % 2 === 1 }">
            <div class="timeline-content">
              <div class="tl-year">{{ item.year }}</div>
              <h3>{{ item.title }}</h3>
              <p>{{ item.text }}</p>
            </div>
            <div class="timeline-dot"></div>
          </div>
        </div>
      </div>
    </section>

    <!-- PRODUCTION -->
    <section class="production-section">
      <div class="container">
        <div class="prod-grid">
          <div class="prod-text">
            <div class="section-label">Производство</div>
            <h2 class="section-title" style="color: var(--white)">Современный завод</h2>
            <p style="color: rgba(255,255,255,0.6)">Производственный комплекс BIBINOR оснащён передовым технологическим оборудованием и функционирует в строгом соответствии с требованиями GMP. Весь производственный цикл — от синтеза активных веществ до фасовки готовой продукции — осуществляется под непрерывным контролем качества.</p>
            <div class="prod-features">
              <div class="prod-feature" v-for="f in prodFeatures" :key="f">
                <svg width="16" height="16" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><polyline points="20 6 9 17 4 12"/></svg>
                {{ f }}
              </div>
            </div>
          </div>
          <div class="prod-image">
            <img src="https://farmak.uz/wp-content/uploads/2023/08/dsc_4985-scaled-1.jpeg" alt="Производство" />
          </div>
        </div>
      </div>
    </section>

    <!-- FACTORY HISTORY + VIDEOS -->
    <section class="factory-section">
      <div class="container">
        <div class="factory-header">
          <div class="section-label">История завода</div>
          <h2 class="section-title">Наш завод в деталях</h2>
          <p class="factory-intro">
            Производственный завод BIBINOR был возведён с нуля и оснащён современным европейским оборудованием. Сегодня это одно из наиболее технически оснащённых ветеринарных фармацевтических предприятий в Центральной Азии. Посмотрите наши видеоматериалы, чтобы узнать больше о производственном процессе и истории компании.
          </p>
        </div>

        <!-- YOUTUBE VIDEOS -->
        <div class="videos-grid">
          <div class="video-card" v-for="video in factoryVideos" :key="video.id">
            <div class="video-wrapper">
              <iframe
                :src="`https://www.youtube.com/embed/${video.youtubeId}`"
                :title="video.title"
                frameborder="0"
                allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share"
                allowfullscreen
              ></iframe>
            </div>
            <div class="video-info">
              <div class="video-tag">{{ video.tag }}</div>
              <h3>{{ video.title }}</h3>
              <p>{{ video.desc }}</p>
            </div>
          </div>
        </div>

        <!-- FACTORY STATS -->
        <div class="factory-stats">
          <div class="fstat" v-for="s in factoryStats" :key="s.label">
            <!-- <div class="fstat-icon">{{ s.icon }}</div> -->
            <div class="fstat-num">{{ s.num }}</div>
            <div class="fstat-label">{{ s.label }}</div>
          </div>
        </div>
      </div>
    </section>

    <!-- TEAM -->
    <section class="team-section">
      <div class="container">
        <div class="section-label" style="text-align:center">Профессионалы</div>
        <h2 class="section-title" style="text-align:center; margin-bottom: 16px">Наша команда</h2>
        <p class="team-subtitle">За каждым препаратом BIBINOR стоит команда высококвалифицированных специалистов — ветеринарных врачей, фармацевтов и учёных.</p>
        <div class="team-grid">
          <div class="team-card" v-for="m in team" :key="m.name">
            <div class="team-avatar">{{ m.initials }}</div>
            <h3>{{ m.name }}</h3>
            <div class="team-pos">{{ m.position }}</div>
            <p>{{ m.bio }}</p>
          </div>
        </div>
      </div>
    </section>

  </div>
</template>

<script setup>
const values = [
  { icon: '🎯', title: 'Миссия', text: 'Обеспечить доступность высококачественных ветеринарных препаратов для каждого животновода Узбекистана.' },
  { icon: '👁️', title: 'Видение', text: 'Стать признанным лидером ветеринарной фармацевтики в Центральной Азии и выйти на международные рынки.' },
  { icon: '💎', title: 'Ценности', text: 'Качество, научная обоснованность, доверие потребителей и непрерывное развитие — фундамент нашей работы.' },
]

const timeline = [
  { year: '1999', title: 'Основание компании', text: 'Создание первой производственной лаборатории и начало разработки ветеринарных препаратов.' },
  { year: '2005', title: 'Первые препараты', text: 'Государственная регистрация первых оригинальных ветеринарных препаратов BIBINOR.' },
  { year: '2010', title: 'Расширение производства', text: 'Строительство современного производственного комплекса и увеличение производственных мощностей.' },
  { year: '2015', title: 'Сертификация GMP', text: 'Получение международного сертификата GMP, подтверждающего соответствие производства мировым стандартам.' },
  { year: '2018', title: 'Сертификат Halal', text: 'Успешное прохождение сертификации Halal, открывшей новые рынки для продукции BIBINOR.' },
  { year: '2024+', title: 'Развитие и инновации', text: 'Продолжение разработки новых препаратов и расширение географии присутствия компании.' },
]

const prodFeatures = [
  'Соответствие стандарту GMP',
  'Многоступенчатый контроль качества',
  'Сертифицированное лабораторное оборудование',
  'Квалифицированный производственный персонал',
  'Строгий входной контроль сырья',
  'Современная система хранения и логистики',
]

// ⚠️ YouTube video ID larini shu yerga kiriting
// Misol: https://www.youtube.com/watch?v=ABC123XYZ => youtubeId: 'ABC123XYZ'
const factoryVideos = [
  {
    id: 1,
    youtubeId: 'KIRITING_1', // <-- 1-video ID sini almashtiring
    tag: 'Производство',
    title: 'Наш производственный завод',
    desc: 'Обзор современного производственного комплекса BIBINOR — от лаборатории до готовой продукции.',
  },
  {
    id: 2,
    youtubeId: 'KIRITING_2', // <-- 2-video ID sini almashtiring
    tag: 'О компании',
    title: 'История компании BIBINOR',
    desc: 'Более 25 лет пути: от основания до лидерства на рынке ветеринарных препаратов Узбекистана.',
  },
  {
    id: 3,
    youtubeId: 'KIRITING_3', // <-- 3-video ID sini almashtiring
    tag: 'Качество',
    title: 'Контроль качества и сертификация',
    desc: 'Как мы обеспечиваем высочайшие стандарты качества на каждом этапе производства препаратов.',
  },
]

const factoryStats = [
  { icon: '🏭', num: '2000+', label: 'кв.м производственных площадей' },
  { icon: '👨‍🔬', num: '50+', label: 'сотрудников на производстве' },
  { icon: '💊', num: '5', label: 'уникальных препаратов' },
  { icon: '📦', num: '1 млн+', label: 'единиц продукции в год' },
]

const team = [
  { initials: 'ДМ', name: 'Директор по производству', position: 'Руководство', bio: 'Более 20 лет опыта в фармацевтической промышленности. Под его руководством производство получило сертификат GMP.' },
  { initials: 'НА', name: 'Главный ветеринар', position: 'Научный отдел', bio: 'Доктор ветеринарных наук, автор ключевых формул препаратов BIBINOR. Специализируется на иммунологии животных.' },
  { initials: 'ФХ', name: 'Начальник ОТК', position: 'Контроль качества', bio: 'Ответственен за соблюдение всех стандартов качества на каждом этапе производственного цикла.' },
]
</script>

<style scoped>
.page-hero {
  position: relative; height: 420px;
  display: flex; align-items: flex-end; padding-bottom: 60px; overflow: hidden;
}
.hero-bg { position: absolute; inset: 0; background-size: cover; background-position: center; }
.hero-overlay { position: absolute; inset: 0; background: linear-gradient(to right, rgba(20,20,100,0.92) 0%, rgba(20,20,100,0.6) 100%); }
.page-hero-content { position: relative; z-index: 1; }
.breadcrumb { display: flex; gap: 10px; align-items: center; margin-bottom: 16px; font-size: 12px; color: rgba(255,255,255,0.5); }
.breadcrumb a { color: var(--gold); text-decoration: none; }
.page-hero-content h1 { font-size: clamp(32px, 5vw, 56px); color: var(--white); margin-bottom: 12px; }
.page-hero-content p { font-size: 16px; color: rgba(255,255,255,0.6); letter-spacing: 1px; }

/* MISSION */
.mission-section { padding: 100px 0; }
.mission-grid { display: grid; grid-template-columns: 1fr 1fr; gap: 80px; align-items: start; }
.mission-text p { font-size: 15px; line-height: 1.8; color: var(--text-body); }
.mission-values { display: flex; flex-direction: column; gap: 2px; }
.value-card { background: var(--off-white); padding: 32px; border-left: 3px solid transparent; transition: border-color 0.3s, transform 0.3s; }
.value-card:hover { border-left-color: var(--gold); transform: translateX(4px); }
.value-icon { font-size: 28px; margin-bottom: 12px; }
.value-card h3 { font-size: 18px; color: var(--navy); margin-bottom: 10px; }
.value-card p { font-size: 14px; color: var(--text-body); line-height: 1.7; }

/* TIMELINE */
.timeline-section { padding: 80px 0; background: var(--off-white); }
.timeline { position: relative; max-width: 900px; margin: 0 auto; }
.timeline::before { content: ''; position: absolute; left: 50%; top: 0; bottom: 0; width: 1px; background: rgba(43,43,143,0.15); transform: translateX(-50%); }
.timeline-item { display: flex; justify-content: flex-end; padding-right: calc(50% + 40px); margin-bottom: 48px; position: relative; }
.timeline-item.right { justify-content: flex-start; padding-right: 0; padding-left: calc(50% + 40px); }
.timeline-content { max-width: 340px; background: var(--white); padding: 28px 32px; border-bottom: 2px solid transparent; transition: border-color 0.3s; }
.timeline-content:hover { border-bottom-color: var(--gold); }
.tl-year { font-family: 'Cormorant Garamond', serif; font-size: 32px; font-weight: 700; color: var(--gold); line-height: 1; margin-bottom: 8px; }
.timeline-content h3 { font-size: 17px; color: var(--navy); margin-bottom: 10px; }
.timeline-content p { font-size: 13px; color: var(--text-body); line-height: 1.7; }
.timeline-dot { position: absolute; left: 50%; top: 28px; width: 12px; height: 12px; background: var(--gold); border: 3px solid var(--off-white); border-radius: 50%; transform: translateX(-50%); }

/* PRODUCTION */
.production-section { background: var(--navy); padding: 100px 0; }
.prod-grid { display: grid; grid-template-columns: 1fr 1fr; gap: 80px; align-items: center; }
.prod-features { margin-top: 32px; display: flex; flex-direction: column; gap: 12px; }
.prod-feature { display: flex; align-items: center; gap: 12px; font-size: 14px; color: rgba(255,255,255,0.6); }
.prod-feature svg { color: var(--gold); flex-shrink: 0; }
.prod-image img { width: 100%; height: 460px; object-fit: cover; }

/* FACTORY SECTION */
.factory-section { padding: 100px 0; background: var(--white); }

.factory-header { text-align: center; max-width: 760px; margin: 0 auto 60px; }

.factory-intro { font-size: 15px; line-height: 1.9; color: var(--text-body); margin-top: 20px; }

/* VIDEOS */
.videos-grid {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 24px;
  margin-bottom: 60px;
}

.video-card {
  background: var(--off-white);
  overflow: hidden;
  transition: transform 0.3s, box-shadow 0.3s;
  border-bottom: 3px solid transparent;
}

.video-card:hover {
  transform: translateY(-6px);
  box-shadow: 0 20px 50px rgba(43,43,143,0.15);
  border-bottom-color: var(--gold);
}

.video-wrapper {
  position: relative;
  width: 100%;
  padding-top: 56.25%;
  background: var(--navy);
  overflow: hidden;
}

.video-wrapper iframe {
  position: absolute;
  top: 0; left: 0;
  width: 100%; height: 100%;
  border: none;
}

.video-info { padding: 24px 28px 28px; }

.video-tag {
  font-size: 10px; font-weight: 600;
  letter-spacing: 3px; text-transform: uppercase;
  color: var(--gold); margin-bottom: 10px;
}

.video-info h3 {
  font-size: 17px; color: var(--navy);
  margin-bottom: 10px; line-height: 1.3;
}

.video-info p { font-size: 13px; color: var(--text-body); line-height: 1.7; }

/* FACTORY STATS */
.factory-stats {
  display: grid;
  grid-template-columns: repeat(4, 1fr);
  background: var(--navy);
}

.fstat {
  padding: 40px 32px; text-align: center;
  border-right: 1px solid rgba(255,255,255,0.07);
  transition: background 0.3s;
}
.fstat:last-child { border-right: none; }
.fstat:hover { background: var(--navy-light); }
.fstat-icon { font-size: 28px; margin-bottom: 12px; }
.fstat-num { font-family: 'Cormorant Garamond', serif; font-size: 34px; font-weight: 700; color: var(--gold); line-height: 1; margin-bottom: 8px; }
.fstat-label { font-size: 12px; color: rgba(255,255,255,0.45); letter-spacing: 1px; line-height: 1.5; }

/* TEAM */
.team-section { padding: 100px 0; background: var(--off-white); }
.team-subtitle { text-align: center; font-size: 15px; color: var(--text-body); max-width: 600px; margin: 0 auto 60px; line-height: 1.8; }
.team-grid { display: grid; grid-template-columns: repeat(3, 1fr); gap: 2px; }
.team-card { background: var(--white); padding: 48px 36px; text-align: center; transition: transform 0.3s; }
.team-card:hover { transform: translateY(-4px); }
.team-avatar { width: 72px; height: 72px; border-radius: 50%; background: var(--navy); color: var(--gold); font-family: 'Cormorant Garamond', serif; font-size: 22px; font-weight: 700; display: flex; align-items: center; justify-content: center; margin: 0 auto 20px; }
.team-card h3 { font-size: 18px; color: var(--navy); margin-bottom: 6px; }
.team-pos { font-size: 11px; font-weight: 600; letter-spacing: 2px; text-transform: uppercase; color: var(--gold); margin-bottom: 16px; }
.team-card p { font-size: 13px; color: var(--text-body); line-height: 1.7; }

@media (max-width: 1024px) {
  .mission-grid, .prod-grid { grid-template-columns: 1fr; }
  .prod-image img { height: 300px; }
  .videos-grid { grid-template-columns: 1fr; }
  .factory-stats { grid-template-columns: 1fr 1fr; }
}
@media (max-width: 768px) {
  .team-grid { grid-template-columns: 1fr; }
  .timeline-item, .timeline-item.right { padding: 0 0 0 40px; justify-content: flex-start; }
  .timeline::before { left: 0; }
  .timeline-dot { left: 0; }
}
@media (max-width: 480px) {
  .factory-stats { grid-template-columns: 1fr; }
}
</style>
