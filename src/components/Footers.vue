<script setup>
</script>

<template>
  <footer class="footer-section">
    <div class="footer-container">
      <div class="footer-top">
        <div class="footer-logo-wrap">
          <img src="@/assets/icons/giarddesignwhite.png" alt="Giarddesign" class="footer-logo" />
        </div>
        <div class="footer-cta-wrap">
          <p class="footer-cta-text">Daj znać, co możemy dla Ciebie zrobić!</p>
          <a href="#" class="footer-btn">Skontaktuj się z nami</a>
        </div>
      </div>

      <div class="footer-divider"></div>

      <div class="footer-middle">
        <nav class="footer-nav">
          <a href="#" class="footer-link">Kontakt</a>
          <a href="#" class="footer-link">Instagram</a>
          <a href="#" class="footer-link">Facebook</a>
          <a href="#" class="footer-link">LinkedIn</a>
        </nav>
        <div class="footer-contact-info">
          <a href="tel:000000000" class="footer-link">000-000-000</a>
          <a href="mailto:giarddesign@kontakt.pl" class="footer-link">giarddesign@kontakt.pl</a>
        </div>
      </div>

      <div class="footer-bottom">
        <p class="footer-copyright">Prawa zastrzeżone © 2022</p>
        <div class="footer-credits">
          <span class="made-by-text">made by</span>
          <img src="@/assets/icons/adrespect.png" alt="AdRespect" class="adrespect-logo" />
        </div>
      </div>
    </div>
  </footer>
</template>

<style scoped>
.footer-section {
  background-color: #111111;
  color: #f5f0ec;
  padding: 80px 0;
  display: flex;
  justify-content: center;
  width: 100%;
  box-sizing: border-box;
}

.footer-container {
  width: 100%;
  max-width: 1440px;
  padding: 0 80px;
  box-sizing: border-box;
  display: flex;
  flex-direction: column;
  margin: 0 auto;
}

.footer-top {
  display: flex;
  justify-content: space-between;
  align-items: center;
  margin-bottom: 62px;
}

.footer-logo {
  height: 19px;
  width: auto;
  display: block;
}

.footer-cta-wrap {
  display: flex;
  align-items: center;
  gap: 24px;
}

.footer-cta-text {
  font-family: 'Inter', sans-serif;
  font-size: 16px;
  line-height: 1.5;
  margin: 0;
  color: #f5f0ec;
}

.footer-btn {
  display: inline-flex;
  align-items: center;
  justify-content: center;
  padding: 0 24px;
  height: 50px;
  background-color: #1b5b31;
  color: #f5f0ec;
  font-family: 'Inter', sans-serif;
  font-size: 16px;
  font-weight: 400;
  text-decoration: none;
  border-radius: 30px;
  border: 1px solid #1b5b31;
  transition: all 0.3s ease;
  box-sizing: border-box;
  white-space: nowrap;
}

.footer-divider {
  width: 100%;
  height: 1px;
  background-color: #f5f0ec;
  margin-bottom: 62px;
  opacity: 0.3;
}

.footer-middle {
  display: flex;
  justify-content: space-between;
  align-items: center;
  margin-bottom: 100px;
}

.footer-nav,
.footer-contact-info {
  display: flex;
  gap: 48px;
  align-items: center;
}

.footer-link {
  font-family: 'Inter', sans-serif;
  font-size: 14px;
  line-height: 1.5;
  color: #f5f0ec;
  text-decoration: none;
  transition: opacity 0.2s ease;
}

.footer-bottom {
  display: flex;
  justify-content: space-between;
  align-items: center;
}

.footer-copyright {
  font-family: 'Inter', sans-serif;
  font-size: 16px;
  line-height: 1.5;
  margin: 0;
  color: #f5f0ec;
}

.footer-credits {
  display: flex;
  align-items: center;
  gap: 16px;
}

.made-by-text {
  font-family: 'Inter', sans-serif;
  font-size: 16px;
  line-height: 1.5;
  color: #f5f0ec;
}

.adrespect-logo {
  height: 23px;
  width: auto;
  display: block;
}

@media (hover: hover) {
  .footer-btn:hover {
    background-color: #f5f0ec;
    color: #1b5b31;
    border-color: #f5f0ec;
  }

  .footer-link:hover {
    opacity: 0.7;
  }
}

.footer-btn:active {
  transform: scale(0.96);
}

@media (max-width: 1199px) {
  .footer-container {
    padding: 0 40px;
  }
}

@media (max-width: 991px) {
  .footer-section {
    padding: 60px 0;
  }

  .footer-container {
    padding: 0 24px;
  }

  .footer-top,
  .footer-middle,
  .footer-bottom {
    flex-direction: column;
    align-items: flex-start;
    gap: 32px;
  }

  .footer-top {
    margin-bottom: 40px;
  }

  .footer-cta-wrap {
    flex-direction: column;
    align-items: flex-start;
    gap: 16px;
    width: 100%;
  }

  .footer-btn {
    width: 100%; 
  }

  .footer-divider {
    margin-bottom: 40px;
  }

  .footer-middle {
    margin-bottom: 60px;
    gap: 32px;
  }

  .footer-nav,
  .footer-contact-info {
    flex-direction: column;
    align-items: flex-start;
    gap: 16px;
  }
}
</style>