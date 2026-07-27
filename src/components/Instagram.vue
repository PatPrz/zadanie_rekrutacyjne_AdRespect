<script setup>
</script>

<template>
  <section class="instagram-section">
    <div class="instagram-container">
      <div class="instagram-card">
        <div class="instagram-inner">
          <div class="instagram-content-left">
            <h2 class="instagram-headline">
              Zostańmy w kontakcie! 
              <span class="headline-line">Znajdziesz nas na <i>Instagramie</i>.</span>
            </h2>
          </div>
          <div class="instagram-content-right">
            <p class="instagram-subtext">
              Śledź nasze<br />
              najnowsze realizacje!
            </p>
            <a href="#" class="instagram-btn">Instagram</a>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<style scoped>
.instagram-section {
  background-color: #f5f0ec;
  padding: 60px 0;
  display: flex;
  justify-content: center;
  width: 100%;
}

.instagram-container {
  width: 100%;
  max-width: 1440px;
  padding: 0 20px;
  display: flex;
  justify-content: center;
}

.instagram-card {
  width: 100%;
  max-width: 1040px;
  min-height: 358px;
  background-color: #1b5b31;
  border-radius: 16px;
  display: flex;
  align-items: center; 
  justify-content: center;
  padding: 60px 80px;
  box-sizing: border-box;
}

.instagram-inner {
  display: flex;
  justify-content: space-between;
  align-items: flex-end; 
  width: 100%;
  gap: 64px;
}

.instagram-content-left {
  flex: 1;
}

.instagram-headline {
  color: #f5f0ec;
  font-family: 'Montserrat', sans-serif;
  font-size: 40px;
  font-weight: 500;
  line-height: 1.2;
  margin: 0;
}

.headline-line {
  display: block;
}

.instagram-headline i {
  font-style: italic;
  font-weight: 700;
}

.instagram-content-right {
  display: flex;
  flex-direction: column;
  gap: 24px;
  flex-shrink: 0;
}

.instagram-subtext {
  color: #f5f0ec;
  font-family: 'Inter', sans-serif;
  font-size: 16px;
  line-height: 1.5;
  margin: 0;
}

.instagram-btn {
  display: inline-flex;
  align-items: center;
  justify-content: center;
  width: 124px;
  height: 46px;
  background-color: #f5f0ec;
  color: #1b5b31;
  font-family: 'Inter', sans-serif;
  font-size: 16px;
  font-weight: 500;
  text-decoration: none;
  border-radius: 30px;
  border: 1px solid transparent;
  transition: all 0.3s ease;
  box-sizing: border-box;
}

@media (hover: hover) {
  .instagram-btn:hover {
    background-color: #1b5b31;
    color: #f5f0ec;
    border-color: #f5f0ec;
    transform: translateY(-2px);
    box-shadow: 0 4px 12px rgba(0, 0, 0, 0.15);
  }
}

.instagram-btn:active {
  transform: scale(0.96);
}

@media (max-width: 1199px) {
  .instagram-card {
    padding: 50px 40px;
  }
}

@media (max-width: 991px) {
  .instagram-card {
    padding: 40px 24px;
    min-height: auto;
  }

  .instagram-inner {
    flex-direction: column;
    align-items: flex-start;
    gap: 32px;
  }
  
  .instagram-headline {
    font-size: 32px;
  }
  
  .instagram-content-right {
    width: 100%;
  }
}

@media (max-width: 576px) {
  .instagram-headline {
    font-size: 26px;
  }

  .instagram-btn {
    width: 100%;
  }
}
</style>