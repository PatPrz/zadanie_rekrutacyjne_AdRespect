<script setup>
import { ref } from 'vue'

const images = [
  new URL('../assets/images/realizacje_1.png', import.meta.url).href,
  new URL('../assets/images/realizacje_2.png', import.meta.url).href,
  new URL('../assets/images/realizacje_3.png', import.meta.url).href,
  new URL('../assets/images/realizacje_4.png', import.meta.url).href,
  new URL('../assets/images/realizacje_5.png', import.meta.url).href,
  new URL('../assets/images/realizacje_6.png', import.meta.url).href,
  new URL('../assets/images/realizacje_7.png', import.meta.url).href,
  new URL('../assets/images/realizacje_8.png', import.meta.url).href,
  new URL('../assets/images/realizacje_9.png', import.meta.url).href,
]

const showAll = ref(false)
const activeIndex = ref(null)

const openLightbox = (index) => {
  activeIndex.value = index
}

const closeLightbox = () => {
  activeIndex.value = null
}

const nextImage = () => {
  if (activeIndex.value !== null) {
    activeIndex.value = (activeIndex.value + 1) % images.length
  }
}

const prevImage = () => {
  if (activeIndex.value !== null) {
    activeIndex.value = (activeIndex.value - 1 + images.length) % images.length
  }
}
</script>

<template>
  <section class="realizacje-section">
    <div class="container">
      <div class="row mb-4 mb-lg-5">
        <div class="col-12">
          <span class="realizacje-subtitle">Realizacje</span>
          <h2 class="realizacje-title mt-2">
            Nasze <i>projekty</i>
          </h2>
        </div>
      </div>

      <div class="masonry-wrapper" :class="{ 'is-collapsed': !showAll }">
        
        <div class="masonry-grid">
          <div 
            v-for="(img, index) in images" 
            :key="index"
            class="masonry-item" 
            @click="openLightbox(index)"
          >
            <img :src="img" alt="Realizacja ogrodu" class="realizacja-img" />
            <div class="img-overlay"><span class="zoom-icon">+</span></div>
          </div>
        </div>

        <div class="fade-gradient" :class="{ 'hidden': showAll }"></div>
      </div>

      <div class="expand-wrapper" :class="{ 'is-expanded': showAll }">
        <button class="btn-expand" @click="showAll = !showAll">
          {{ showAll ? 'Zwiń' : 'Rozwiń' }}
          <svg width="16" height="16" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" :class="{ 'rotated': showAll }">
            <line x1="12" y1="5" x2="12" y2="19"></line>
            <polyline points="19 12 12 19 5 12"></polyline>
          </svg>
        </button>
      </div>
    </div>

    <div v-if="activeIndex !== null" class="lightbox-overlay" @click.self="closeLightbox">
      <button class="lightbox-close" @click="closeLightbox" aria-label="Zamknij">&times;</button>
      <button class="lightbox-prev" @click="prevImage" aria-label="Poprzednie">&#10094;</button>
      
      <div class="lightbox-content">
        <img :src="images[activeIndex]" alt="Powiększona realizacja" />
        <span class="lightbox-counter">{{ activeIndex + 1 }} / {{ images.length }}</span>
      </div>

      <button class="lightbox-next" @click="nextImage" aria-label="Następne">&#10095;</button>
    </div>
  </section>
</template>

<style scoped>
.realizacje-section {
  background-color: #dcc1ab;
  padding: 120px 0 80px;
  position: relative;
  overflow: hidden;
}

.realizacje-subtitle {
  color: #1b5b31;
  font-family: 'Inter', sans-serif;
  font-size: 12px;
  display: block;
}

.realizacje-title {
  color: #111;
  font-family: 'Montserrat', sans-serif;
  font-size: 48px;
  font-weight: 500;
}

.realizacje-title i {
  font-style: italic;
  font-weight: 400;
}

.masonry-wrapper {
  position: relative;
  max-height: 3000px;
  overflow: hidden;
  transition: max-height 0.8s cubic-bezier(0.4, 0, 0.2, 1);
}

.masonry-wrapper.is-collapsed {
  max-height: 950px;
}

.masonry-grid {
  column-count: 3;
  column-gap: 24px;
  margin-bottom: 40px;
}

.masonry-item {
  position: relative;
  border-radius: 12px;
  overflow: hidden;
  cursor: pointer;
  background: rgba(255, 255, 255, 0.1);
  margin-bottom: 24px;
  break-inside: avoid; 
  transform: translateZ(0); 
}

.realizacja-img {
  width: 100%;
  height: auto;
  display: block;
  transition: transform 0.4s ease;
}

.img-overlay {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background: rgba(17, 17, 17, 0.3);
  display: flex;
  align-items: center;
  justify-content: center;
  opacity: 0;
  transition: opacity 0.3s ease;
}

.zoom-icon {
  color: #fff;
  font-size: 36px;
  font-weight: 300;
  border: 2px solid #fff;
  width: 50px;
  height: 50px;
  border-radius: 50%;
  display: flex;
  align-items: center;
  justify-content: center;
}

@media (hover: hover) {
  .masonry-item:hover .realizacja-img {
    transform: scale(1.03);
  }
  .masonry-item:hover .img-overlay {
    opacity: 1;
  }
  .btn-expand:hover {
    background: #111;
    color: #dcc1ab;
  }
  .lightbox-prev:hover,
  .lightbox-next:hover {
    background: rgba(255, 255, 255, 0.3);
  }
  .lightbox-close:hover {
    color: #dcc1ab;
  }
}

.masonry-item:active .realizacja-img {
  transform: scale(0.98);
}
.btn-expand:active {
  transform: scale(0.96);
}

.fade-gradient {
  position: absolute;
  bottom: 0;
  left: 0;
  width: 100%;
  height: 350px;
  background: linear-gradient(to bottom, rgba(220, 193, 171, 0), rgba(220, 193, 171, 1) 90%);
  pointer-events: none;
  opacity: 1;
  transition: opacity 0.4s ease;
}

.fade-gradient.hidden {
  opacity: 0;
  pointer-events: none;
}

.expand-wrapper {
  position: relative;
  text-align: center;
  margin-top: -50px;
  padding-bottom: 20px;
  z-index: 5;
  transition: margin-top 0.8s ease;
}

.expand-wrapper.is-expanded {
  margin-top: 20px;
}

.btn-expand {
  background: transparent;
  border: 1px solid #111;
  color: #111;
  font-family: 'Inter', sans-serif;
  font-size: 16px;
  padding: 12px 32px;
  border-radius: 30px;
  cursor: pointer;
  display: inline-flex;
  align-items: center;
  gap: 8px;
  transition: all 0.3s ease;
}

.btn-expand svg {
  transition: transform 0.3s ease;
}

.btn-expand svg.rotated {
  transform: rotate(180deg);
}

.lightbox-overlay {
  position: fixed;
  top: 0;
  left: 0;
  width: 100vw;
  height: 100vh;
  background: rgba(0, 0, 0, 0.9);
  z-index: 9999;
  display: flex;
  align-items: center;
  justify-content: center;
}

.lightbox-content {
  position: relative;
  max-width: 80vw;
  max-height: 85vh;
  text-align: center;
}

.lightbox-content img {
  max-width: 100%;
  max-height: 80vh;
  object-fit: contain;
  border-radius: 8px;
  box-shadow: 0 10px 30px rgba(0,0,0,0.5);
}

.lightbox-counter {
  color: #fff;
  display: block;
  margin-top: 12px;
  font-family: 'Inter', sans-serif;
  font-size: 14px;
}

.lightbox-close {
  position: absolute;
  top: 20px;
  right: 30px;
  background: none;
  border: none;
  color: #fff;
  font-size: 44px;
  cursor: pointer;
  z-index: 10000;
  transition: color 0.3s;
}

.lightbox-prev,
.lightbox-next {
  position: absolute;
  top: 50%;
  transform: translateY(-50%);
  background: rgba(255, 255, 255, 0.1);
  border: none;
  color: #fff;
  font-size: 24px;
  width: 50px;
  height: 50px;
  cursor: pointer;
  border-radius: 50%;
  transition: background 0.3s;
  z-index: 10000;
  display: flex;
  align-items: center;
  justify-content: center;
}

.lightbox-prev { left: 40px; }
.lightbox-next { right: 40px; }

@media (max-width: 991px) {
  .realizacje-section {
    padding: 80px 0 60px;
  }
  
  .realizacje-title {
    font-size: 38px;
  }
  
  .masonry-grid {
    column-count: 2;
    column-gap: 16px;
  }
  
  .masonry-item {
    margin-bottom: 16px;
  }
  
  .masonry-wrapper.is-collapsed {
    max-height: 750px; 
  }

  .lightbox-prev { left: 20px; }
  .lightbox-next { right: 20px; }
  .lightbox-close { top: 15px; right: 20px; font-size: 36px; }
}

@media (max-width: 767px) {
  .realizacje-section {
    padding: 60px 0 50px;
  }
  
  .realizacje-title {
    font-size: 30px;
  }
  
  .masonry-grid {
    column-count: 1;
    margin-bottom: 24px;
  }
  
  .masonry-wrapper.is-collapsed {
    max-height: 600px;
  }

  .lightbox-content { max-width: 95vw; }
  .lightbox-prev { left: 10px; width: 40px; height: 40px; }
  .lightbox-next { right: 10px; width: 40px; height: 40px; }
}
</style>