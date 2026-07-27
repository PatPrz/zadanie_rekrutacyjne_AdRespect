<script setup>
import { ref } from 'vue'

import pencilIcon from '../assets/icons/pencil.png'
import eyeIcon from '../assets/icons/eye.png'
import starsIcon from '../assets/icons/stars.png'

const cards = ref([
  {
    id: 1,
    title: 'Projekty',
    description:
      'Zaprojektujemy Twój ogród w nowoczesnym stylu i z najlepszym wykorzystaniem istniejącej przestrzeni.',
    linkText: 'Dowiedz się więcej',
    linkUrl: '#',
    icon: pencilIcon,
  },
  {
    id: 2,
    title: 'Wizualizacje',
    description:
      'Przedstawimy Ci projekty koncepcyjne w postaci wirtualnego spaceru animowanego w technologii 3D.',
    linkText: 'Dowiedz się więcej',
    linkUrl: '#',
    icon: eyeIcon,
  },
  {
    id: 3,
    title: 'Realizacje',
    description:
      'Zrealizujemy Twoje marzenie przy użyciu najnowszych rozwiązań i zaawansowanych technologii.',
    linkText: 'Zobacz nasze realizacje',
    linkUrl: '#',
    icon: starsIcon,
  },
])
</script>

<template>
  <section class="oferta-section">
    <div class="container">
      <div class="row mb-4 mb-lg-5">
        <div class="col-lg-9 col-xl-8">
          <span class="oferta-subtitle">Oferta</span>
          <h2 class="oferta-title mt-2 mb-3 mb-md-4">Działamy <i>kompleksowo</i></h2>
          <p class="oferta-description">
            Oferujemy kompletną obsługę inwestycji terenów zielonych. Projektujemy nowoczesne ogrody
            przydomowe oraz rezydencjonalne. Stworzymy dla Ciebie projekt, zwizualizujemy go i
            wcielimy w życie, a na każdym etapie posłużymy radą i wieloletnim doświadczeniem.
          </p>
        </div>
      </div>

      <div class="row g-3 g-lg-4 mt-2">
        <div class="col-12 col-md-4" v-for="card in cards" :key="card.id">
          <a :href="card.linkUrl" class="card-link-wrapper">
            <div class="oferta-card h-100">
              <div class="card-icon mb-3 mb-md-4">
                <img :src="card.icon" :alt="card.title + ' ikona'" class="icon-img" />
              </div>

              <h3 class="card-title">{{ card.title }}</h3>
              <p class="card-desc">{{ card.description }}</p>

              <div class="card-action mt-auto">
                <span class="action-text">{{ card.linkText }}</span>
                <span class="action-arrow">
                  <svg
                    width="16"
                    height="16"
                    viewBox="0 0 24 24"
                    fill="none"
                    stroke="currentColor"
                    stroke-width="2"
                    stroke-linecap="round"
                    stroke-linejoin="round"
                  >
                    <line x1="5" y1="12" x2="19" y2="12"></line>
                    <polyline points="12 5 19 12 12 19"></polyline>
                  </svg>
                </span>
              </div>
            </div>
          </a>
        </div>
      </div>
    </div>
  </section>
</template>

<style scoped>
.oferta-section {
  background-color: #f5f0ec;
  padding: 120px 0 160px;
}

.oferta-subtitle {
  color: #1b5b31;
  font-family: 'Inter', sans-serif;
  font-size: 12px;
  line-height: 1.5;
  display: block;
}

.oferta-title {
  color: #111;
  font-family: 'Montserrat', sans-serif;
  font-size: 48px;
  font-weight: 500;
  line-height: 1.15;
}

.oferta-title i {
  font-style: italic;
  font-weight: 400;
}

.oferta-description {
  color: #111;
  font-family: 'Inter', sans-serif;
  font-size: 16px;
  line-height: 1.5;
  margin: 0;
  max-width: 702px;
}

.card-link-wrapper {
  text-decoration: none;
  display: block;
  height: 100%;
}

.oferta-card {
  background-color: #ffffff;
  border-radius: 24px;
  padding: 48px 40px;
  display: flex;
  flex-direction: column;
  transition:
    transform 0.3s ease,
    box-shadow 0.3s ease;
}

.icon-img {
  width: 44px;
  height: 44px;
  object-fit: contain;
}

.card-title {
  color: #111;
  font-family: 'Montserrat', sans-serif;
  font-size: 28px;
  font-weight: 500;
  line-height: 1.15;
  margin-bottom: 12px;
}

.card-desc {
  color: #111;
  font-family: 'Inter', sans-serif;
  font-size: 14px;
  line-height: 1.5;
  margin-bottom: 32px;
}

.card-action {
  display: inline-flex;
  align-items: center;
  gap: 8px;
  color: #1b5b31;
  font-family: 'Inter', sans-serif;
  font-size: 16px;
  border-bottom: 1px solid #1b5b31;
  padding-bottom: 4px;
  width: max-content;
  transition:
    color 0.3s ease,
    border-color 0.3s ease;
}

.action-arrow {
  display: flex;
  transition: transform 0.3s ease;
}

@media (hover: hover) {
  .card-link-wrapper:hover .oferta-card {
    transform: translateY(-8px);
    box-shadow: 0 15px 35px rgba(27, 91, 49, 0.08);
  }

  .card-link-wrapper:hover .action-arrow {
    transform: translateX(6px);
  }
}

.card-link-wrapper:active .oferta-card {
  transform: scale(0.98);
}

@media (max-width: 1199px) {
  .oferta-card {
    padding: 36px 28px;
  }

  .card-title {
    font-size: 24px;
  }
}

@media (max-width: 991px) {
  .oferta-section {
    padding: 80px 0 100px;
  }

  .oferta-title {
    font-size: 38px;
  }

  .oferta-card {
    padding: 32px 20px;
    border-radius: 20px;
  }

  .card-title {
    font-size: 22px;
  }

  .card-desc {
    font-size: 13px;
    margin-bottom: 24px;
  }

  .card-action {
    font-size: 14px;
  }
}

@media (max-width: 767px) {
  .oferta-section {
    padding: 60px 0 70px;
  }

  .oferta-title {
    font-size: 30px;
  }

  .oferta-description {
    font-size: 15px;
  }

  .oferta-card {
    padding: 32px 24px;
  }

  .card-title {
    font-size: 24px;
  }

  .card-desc {
    font-size: 14px;
  }
}
</style>