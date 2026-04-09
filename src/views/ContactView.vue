<template>
  <div class="contact-page">

    <section class="page-hero">
      <div class="hero-bg" style="background-image: url('https://images.unsplash.com/photo-1529242406-97e9e2e97d0a?w=1400&q=80')"></div>
      <div class="hero-overlay"></div>
      <div class="container">
        <div class="page-hero-content">
          <div class="breadcrumb">
            <RouterLink to="/">Главная</RouterLink><span>/</span><span>Контакты</span>
          </div>
          <h1>Свяжитесь с нами</h1>
          <p>Мы всегда рады помочь и ответить на ваши вопросы</p>
        </div>
      </div>
    </section>

    <section class="contact-main">
      <div class="container">
        <div class="contact-grid">

          <!-- FORM -->
          <div class="form-section">
            <div class="section-label">Обратная связь</div>
            <h2 class="section-title">Напишите нам</h2>
            <p class="form-desc">Заполните форму, и наш специалист свяжется с вами в течение рабочего дня.</p>

            <form class="contact-form" @submit.prevent="submitForm">
              <div class="form-row">
                <div class="form-group">
                  <label>Ваше имя *</label>
                  <input v-model="form.name" type="text" placeholder="Иванов Иван" required />
                </div>
                <div class="form-group">
                  <label>Телефон *</label>
                  <input v-model="form.phone" type="tel" placeholder="+998 XX XXX XX XX" required />
                </div>
              </div>
              <div class="form-group">
                <label>Email</label>
                <input v-model="form.email" type="email" placeholder="example@mail.com" />
              </div>
              <div class="form-group">
                <label>Тема обращения</label>
                <select v-model="form.subject">
                  <option value="">Выберите тему</option>
                  <option>Вопрос о препарате</option>
                  <option>Стать дистрибьютором</option>
                  <option>Сотрудничество</option>
                  <option>Запрос документов</option>
                  <option>Другое</option>
                </select>
              </div>
              <div class="form-group">
                <label>Сообщение *</label>
                <textarea v-model="form.message" rows="5" placeholder="Опишите ваш вопрос или предложение..." required></textarea>
              </div>

              <div v-if="submitted" class="success-msg">
                ✓ Ваше сообщение отправлено! Мы свяжемся с вами в ближайшее время.
              </div>

              <button type="submit" class="btn-primary submit-btn" :disabled="submitted">
                {{ submitted ? 'Отправлено ✓' : 'Отправить сообщение' }}
              </button>
            </form>
          </div>

          <!-- INFO -->
          <div class="info-section">
            <div class="info-card">
              <h3>Контактная информация</h3>

              <div class="info-item">
                <div class="info-icon">
                  <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.5"><path d="M22 16.92v3a2 2 0 01-2.18 2 19.79 19.79 0 01-8.63-3.07A19.5 19.5 0 014.5 11.5a19.79 19.79 0 01-3.07-8.67A2 2 0 013.44 1h3a2 2 0 012 1.72c.127.96.361 1.903.7 2.81a2 2 0 01-.45 2.11L7.91 8.91a16 16 0 006.29 6.29l1.28-1.28a2 2 0 012.11-.45c.907.339 1.85.573 2.81.7A2 2 0 0122 16.92z"/></svg>
                </div>
                <div>
                  <div class="info-label">Телефон</div>
                  <a href="tel:+998995203040" class="info-value">+998 99 520 30 40</a>
                </div>
              </div>

              <div class="info-item">
                <div class="info-icon">
                  <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.5"><path d="M4 4h16c1.1 0 2 .9 2 2v12c0 1.1-.9 2-2 2H4c-1.1 0-2-.9-2-2V6c0-1.1.9-2 2-2z"/><polyline points="22,6 12,13 2,6"/></svg>
                </div>
                <div>
                  <div class="info-label">Email</div>
                  <a href="mailto:bibinorpharm@gmail.com" class="info-value">bibinorpharm@gmail.com</a>
                </div>
              </div>

              <div class="info-item">
                <div class="info-icon">
                  <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.5"><path d="M21 10c0 7-9 13-9 13s-9-6-9-13a9 9 0 0118 0z"/><circle cx="12" cy="10" r="3"/></svg>
                </div>
                <div>
                  <div class="info-label">Адрес</div>
                  <div class="info-value">Республика Узбекистан</div>
                </div>
              </div>

              <div class="info-item">
                <div class="info-icon">
                  <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.5"><circle cx="12" cy="12" r="10"/><polyline points="12 6 12 12 16 14"/></svg>
                </div>
                <div>
                  <div class="info-label">Режим работы</div>
                  <div class="info-value">Пн–Пт: 09:00 – 18:00</div>
                  <div class="info-value" style="color: var(--gray); font-size: 13px;">Сб: 09:00 – 14:00</div>
                </div>
              </div>
            </div>

            <div class="dealer-card">
              <h3>Стать дистрибьютором</h3>
              <p>Мы ищем надёжных дистрибьюторов в регионах Узбекистана и за рубежом. Предлагаем выгодные условия сотрудничества и полную поддержку.</p>
              <ul class="dealer-benefits">
                <li><span>✓</span> Конкурентоспособные цены</li>
                <li><span>✓</span> Маркетинговая поддержка</li>
                <li><span>✓</span> Техническое обучение</li>
                <li><span>✓</span> Эксклюзивные территории</li>
              </ul>
            </div>
          </div>
        </div>
      </div>
    </section>

  </div>
</template>

<script setup>
import { ref } from 'vue'

const form = ref({ name: '', phone: '', email: '', subject: '', message: '' })
const submitted = ref(false)

const submitForm = () => {
  submitted.value = true
  setTimeout(() => { submitted.value = false; form.value = { name: '', phone: '', email: '', subject: '', message: '' } }, 5000)
}
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

.contact-main { padding: 80px 0 100px; }

.contact-grid {
  display: grid;
  grid-template-columns: 1fr 400px;
  gap: 60px;
  align-items: start;
}

.form-desc {
  font-size: 14px;
  color: var(--text-body);
  line-height: 1.8;
  margin-top: 16px;
  margin-bottom: 36px;
}

.contact-form { display: flex; flex-direction: column; gap: 20px; }

.form-row { display: grid; grid-template-columns: 1fr 1fr; gap: 20px; }

.form-group { display: flex; flex-direction: column; gap: 8px; }

.form-group label {
  font-size: 11px;
  font-weight: 600;
  letter-spacing: 2px;
  text-transform: uppercase;
  color: var(--navy);
}

.form-group input,
.form-group select,
.form-group textarea {
  font-family: 'Jost', sans-serif;
  font-size: 14px;
  color: var(--text-dark);
  background: var(--off-white);
  border: 1px solid transparent;
  border-bottom: 1px solid rgba(11,29,53,0.2);
  padding: 14px 16px;
  outline: none;
  transition: all 0.3s;
  width: 100%;
  resize: vertical;
}

.form-group input:focus,
.form-group select:focus,
.form-group textarea:focus {
  border-color: var(--gold);
  background: var(--white);
}

.submit-btn {
  width: 100%;
  justify-content: center;
  padding: 18px;
  font-size: 12px;
}

.submit-btn:disabled {
  background: var(--gray);
  cursor: not-allowed;
  transform: none;
}

.success-msg {
  background: #e8f5e9;
  border-left: 3px solid #4caf50;
  padding: 16px 20px;
  font-size: 14px;
  color: #2e7d32;
}

/* INFO */
.info-card, .dealer-card {
  background: var(--off-white);
  padding: 40px;
  margin-bottom: 2px;
}

.info-card h3, .dealer-card h3 {
  font-size: 14px;
  font-weight: 600;
  letter-spacing: 2px;
  text-transform: uppercase;
  color: var(--navy);
  margin-bottom: 28px;
  padding-bottom: 16px;
  border-bottom: 1px solid rgba(11,29,53,0.1);
}

.info-item {
  display: flex;
  gap: 16px;
  margin-bottom: 24px;
  align-items: flex-start;
}

.info-item:last-child { margin-bottom: 0; }

.info-icon {
  width: 40px;
  height: 40px;
  background: var(--navy);
  display: flex;
  align-items: center;
  justify-content: center;
  flex-shrink: 0;
}

.info-icon svg {
  width: 18px;
  height: 18px;
  color: var(--gold);
}

.info-label {
  font-size: 10px;
  font-weight: 600;
  letter-spacing: 2px;
  text-transform: uppercase;
  color: var(--gray);
  margin-bottom: 4px;
}

.info-value {
  font-size: 15px;
  color: var(--navy);
  font-weight: 500;
  text-decoration: none;
  transition: color 0.3s;
  display: block;
}

a.info-value:hover { color: var(--gold); }

.dealer-card { background: var(--navy); }
.dealer-card h3 { color: var(--white); border-color: rgba(255,255,255,0.1); }
.dealer-card p { font-size: 14px; color: rgba(255,255,255,0.5); line-height: 1.8; margin-bottom: 24px; }

.dealer-benefits { list-style: none; display: flex; flex-direction: column; gap: 10px; }

.dealer-benefits li {
  display: flex;
  gap: 12px;
  font-size: 13px;
  color: rgba(255,255,255,0.6);
  align-items: center;
}

.dealer-benefits li span { color: var(--gold); font-weight: 700; }

@media (max-width: 900px) {
  .contact-grid { grid-template-columns: 1fr; }
  .form-row { grid-template-columns: 1fr; }
}
</style>
