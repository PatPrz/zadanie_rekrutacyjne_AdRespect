<script setup>
import oFirmieImg from '../assets/images/o_firmie.png'
</script>

<template>
  <section class="o-firmie-section">
    <div class="image-half">
      <img :src="oFirmieImg" alt="O firmie GiardDesign" class="mirrored-image" />
    </div>

    <div class="container relative-container h-100">
      <div class="row h-100 align-items-center">
        <div class="col-12 col-lg-6 offset-lg-6">
          <div class="content-wrapper">
            <span class="subtitle">O firmie</span>
            <h2 class="title mt-2 mb-3 mb-md-4">
              Tworzymy <br />
              <i>z pasją</i>
            </h2>
            <p class="description mb-4 mb-lg-5">
              Każdy projekt to nowe wyzwanie. Dlatego nasz zespół tworzą wykwalifikowani projektanci oraz architekci, których zadaniem jest rozpoznanie i realizacja potrzeb każdego Klienta. Nasza specjalizacja to przestrzenie nowoczesne, które charakteryzuje minimalizm, geometria i elegancka prostota. Tworzymy ogrody małoobsługowe, dostosowane do współczesnego trybu życia.
            </p>
            
            <a href="#" class="btn-outline-light">
              <span>Poznaj nas bliżej</span>
              <svg width="16" height="16" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round">
                <line x1="5" y1="12" x2="19" y2="12"></line>
                <polyline points="12 5 19 12 12 19"></polyline>
              </svg>
            </a>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<style scoped>
.o-firmie-section {
  background-color: #1b5b31; 
  color: #f5f0ec;
  position: relative;
  min-height: 720px; 
  overflow: hidden;
}

.image-half {
  position: absolute;
  top: 0;
  left: 0;
  width: 50%;
  height: 100%;
  z-index: 1;
}

.mirrored-image {
  width: 100%;
  height: 100%;
  object-fit: cover;
  transform: scaleX(-1);
  display: block;
}

.relative-container {
  position: relative;
  z-index: 2; 
}

.content-wrapper {
  padding-left: 80px;
  padding-top: 120px;
  padding-bottom: 120px;
}

.subtitle {
  font-family: 'Inter', sans-serif;
  font-size: 12px;
  font-weight: 400;
  line-height: 1.5;
  display: block;
}

.title {
  font-family: 'Montserrat', sans-serif;
  font-size: 48px;
  font-weight: 500;
  line-height: 1.15;
}

.title i {
  font-style: italic;
  font-weight: 400;
}

.description {
  font-family: 'Inter', sans-serif;
  font-size: 16px;
  font-weight: 400;
  line-height: 1.5;
  max-width: 490px;
}

.btn-outline-light {
  display: inline-flex;
  justify-content: center;
  align-items: center;
  gap: 12px; 
  padding: 0 24px;
  height: 50px;
  border: 1px solid #f5f0ec;
  border-radius: 30px;
  background: transparent;
  color: #f5f0ec;
  font-family: 'Inter', sans-serif;
  font-size: 16px;
  text-decoration: none;
  transition: all 0.3s ease;
  box-sizing: border-box;
}

.btn-outline-light svg {
  transition: transform 0.3s ease;
}

@media (hover: hover) {
  .btn-outline-light:hover {
    background-color: #f5f0ec;
    color: #1b5b31;
  }

  .btn-outline-light:hover svg {
    transform: translateX(4px);
  }
}

.btn-outline-light:active {
  transform: scale(0.96);
}

@media (max-width: 1199px) {
  .content-wrapper {
    padding-left: 30px;
    padding-top: 80px;
    padding-bottom: 80px;
  }

  .title {
    font-size: 40px;
  }
}

@media (max-width: 991px) {
  .o-firmie-section {
    min-height: auto;
  }

  .image-half {
    position: relative;
    width: 100%;
    height: 380px;
  }

  .content-wrapper {
    padding-left: 0;
    padding-top: 60px;
    padding-bottom: 60px;
  }

  .title {
    font-size: 36px;
  }

  .description {
    max-width: 100%;
  }
}

@media (max-width: 576px) {
  .image-half {
    height: 280px;
  }

  .content-wrapper {
    padding-top: 40px;
    padding-bottom: 50px;
  }

  .title {
    font-size: 30px;
  }

  .btn-outline-light {
    width: 100%;
  }
}
</style>