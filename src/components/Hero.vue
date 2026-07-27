<script setup>
import { ref, computed } from 'vue'

const slides = [
  {
    title: 'Nowoczesna aranżacja Twojego ogrodu',
    text: 'Marka GiardDesign to wieloletnie doświadczenie i wysoka estetyka realizacji. Oferujemy kompleksowy zakres usług z indywidualnym podejściem do każdego projektu.',
    image: new URL('../assets/images/hero.png', import.meta.url).href,
  },
]

const currentSlide = ref(0)
const slideDirection = ref('slide-left')
const transitionKey = ref(0)

const currentSlideData = computed(() => slides[currentSlide.value])

function nextSlide() {
  slideDirection.value = 'slide-left'
  currentSlide.value = (currentSlide.value + 1) % slides.length
  transitionKey.value++
}

function prevSlide() {
  slideDirection.value = 'slide-right'
  currentSlide.value = (currentSlide.value - 1 + slides.length) % slides.length
  transitionKey.value++
}
</script>

<template>
  <section class="hero">
    <transition :name="slideDirection">
      <div class="slide-layer" :key="transitionKey">
        
        <div class="container hero-container">
          <div class="hero-left">
            <div class="content">
              <h1>{{ currentSlideData.title }}</h1>
              <p>{{ currentSlideData.text }}</p>

              <div class="buttons">
                <a href="#" class="btn-green">Skontaktuj się z nami</a>
                <a href="#" class="btn-outline">Zobacz nasze realizacje ↓</a>
              </div>
            </div>
          </div>
        </div>

        <div class="hero-right">
          <img :src="currentSlideData.image" alt="Realizacja ogrodu" />
        </div>

      </div>
    </transition>

    <div class="slider-nav">
      <button @click="prevSlide" aria-label="Poprzedni slajd">←</button>
      <button @click="nextSlide" aria-label="Następny slajd">→</button>
    </div>
  </section>
</template>

<style scoped>
.hero {
  position: relative;
  display: grid;
  grid-template-columns: 1fr;
  background: #dcc1ab;
  overflow: hidden;
  min-height: 737px;
}

.slide-layer {
  grid-area: 1 / 1;
  display: flex;
  width: 100%;
  position: relative;
}

.hero-container {
  display: flex;
  align-items: center;
  flex: 1;
  position: relative;
  z-index: 2;
  pointer-events: none;
}

.hero-left {
  width: 50%;
  display: flex;
  align-items: center;
  pointer-events: auto; 
}

.content {
  width: 100%;
  max-width: 599px;
}

.content h1 {
  font-family: 'Montserrat', sans-serif;
  font-size: 60px;
  font-weight: 500;
  line-height: 1.16;
  color: #111;
  max-width: 520px;
}

.content p {
  margin-top: 44px;
  max-width: 490px;
  font-family: 'Inter', sans-serif;
  font-size: 16px;
  line-height: 1.5;
  margin-bottom: 72px;
  color: #111;
}

.buttons {
  display: flex;
  gap: 24px;
  flex-wrap: wrap;
}

.btn-green {
  width: 208px;
  height: 50px;
  border: none;
  border-radius: 30px;
  background: #1b5b31;
  color: #f5f0ec;
  font-family: 'Inter', sans-serif;
  font-size: 16px;
  cursor: pointer;
  display: flex;
  justify-content: center;
  align-items: center;
  text-decoration: none;
  transition: all 0.3s ease;
  box-sizing: border-box;
}

.btn-green:hover {
  background: #dcc1ab;
  color: #1b5b31;
  border: 1px solid #1b5b31;
}

.btn-outline {
  width: 249px;
  height: 50px;
  background: none;
  border: 1px solid #1b5b31;
  border-radius: 30px;
  color: #1b5b31;
  font-family: 'Inter', sans-serif;
  font-size: 16px;
  cursor: pointer;
  display: flex;
  justify-content: center;
  align-items: center;
  text-decoration: none;
  transition: all 0.3s ease;
  box-sizing: border-box;
}

.btn-outline:hover {
  background: #1b5b31;
  color: #f5f0ec;
}

.hero-right {
  position: absolute;
  top: 0;
  right: 0;
  width: 48%; 
  height: 100%;
  z-index: 1;
}

.hero-right img {
  width: 100%;
  height: 100%;
  object-fit: cover;
  display: block;
}

.slider-nav {
  position: absolute;
  right: 0;
  bottom: 0;
  width: 192px;
  height: 96px;
  background: #f5f0ec;
  display: flex;
  z-index: 20;
}

.slider-nav button {
  width: 96px;
  height: 96px;
  border: none;
  background: none;
  font-size: 34px;
  cursor: pointer;
  transition: background 0.2s ease;
  display: flex;
  align-items: center;
  justify-content: center;
}

.slider-nav button:hover {
  background: #ece3db;
}

.slide-left-enter-active,
.slide-left-leave-active,
.slide-right-enter-active,
.slide-right-leave-active {
  transition: transform 0.6s cubic-bezier(0.4, 0, 0.2, 1);
}

.slide-left-enter-from { transform: translateX(100%); }
.slide-left-leave-to { transform: translateX(-100%); }
.slide-right-enter-from { transform: translateX(-100%); }
.slide-right-leave-to { transform: translateX(100%); }

@media (max-width: 991px) {
  .hero {
    min-height: auto;
  }

  .slide-layer {
    flex-direction: column;
  }

  .hero-container {
    padding-top: 60px;
    padding-bottom: 40px;
  }

  .hero-left {
    width: 100%;
  }

  .content h1 {
    font-size: 36px;
    max-width: 100%;
  }

  .content p {
    margin-top: 20px;
    margin-bottom: 32px;
    max-width: 100%;
  }

  .hero-right {
    position: relative;
    width: 100%;
    height: 350px;
  }

  .slider-nav {
    width: 120px;
    height: 60px;
  }

  .slider-nav button {
    width: 60px;
    height: 60px;
    font-size: 24px;
  }
}

@media (max-width: 576px) {
  .hero-container {
    padding-top: 40px;
    padding-bottom: 30px;
  }

  .content h1 {
    font-size: 28px;
  }

  .buttons {
    flex-direction: column;
    gap: 12px;
    width: 100%;
  }

  .btn-green,
  .btn-outline {
    width: 100%;
  }

  .hero-right {
    height: 280px;
  }
}
</style>