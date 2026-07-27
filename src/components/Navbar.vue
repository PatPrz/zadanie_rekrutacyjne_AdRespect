<script setup>
import { ref, onMounted, onBeforeUnmount } from 'vue'

const searchOpen = ref(false)
const dropdownOpen = ref(false)
const mobileMenuOpen = ref(false)

const rightSideRef = ref(null)

function toggleSearch() {
  searchOpen.value = !searchOpen.value
  if (searchOpen.value) {
    dropdownOpen.value = false
  }
}

function toggleDropdown() {
  dropdownOpen.value = !dropdownOpen.value
}

function toggleMobileMenu() {
  mobileMenuOpen.value = !mobileMenuOpen.value
  if (mobileMenuOpen.value) {
    searchOpen.value = false
  }
}

function closeMobileMenu() {
  mobileMenuOpen.value = false
  dropdownOpen.value = false
  searchOpen.value = false
}

function handleClickOutside(event) {
  if (rightSideRef.value && !rightSideRef.value.contains(event.target)) {
    searchOpen.value = false
    dropdownOpen.value = false
  }
}

onMounted(() => {
  document.addEventListener('click', handleClickOutside)
})

onBeforeUnmount(() => {
  document.removeEventListener('click', handleClickOutside)
})
</script>

<template>
  <header class="navbar-wrapper">
    <div class="container">
      <nav class="navbar-content" ref="rightSideRef">
        <div class="logo">
          <a href="#" @click="closeMobileMenu">
            <img src="../assets/icons/giarddesignblack.png" alt="GiardDesign" />
          </a>
        </div>

        <div class="right-side">
          
          <div class="nav-menu" :class="{ 'is-open': mobileMenuOpen }">
            <ul class="nav-list">
              <li class="dropdown-custom">
                <button class="nav-button" @click="toggleDropdown">
                  Oferta
                  <span class="arrow" :class="{ rotate: dropdownOpen }">▼</span>
                </button>

                <transition name="dropdown">
                  <div v-if="dropdownOpen" class="dropdown-box">
                    <a href="#" @click="closeMobileMenu">Projektowanie</a>
                    <a href="#" @click="closeMobileMenu">Wizualizacje</a>
                    <a href="#" @click="closeMobileMenu">Realizacje</a>
                    <a href="#" @click="closeMobileMenu">Pielęgnacja</a>
                  </div>
                </transition>
              </li>

              <li>
                <a href="#" @click="closeMobileMenu">O firmie</a>
              </li>

              <li>
                <a href="#" @click="closeMobileMenu">Realizacje</a>
              </li>

              <li>
                <a href="#" @click="closeMobileMenu">Kontakt</a>
              </li>
            </ul>
          </div>

          <div class="nav-actions">
            <div class="search-wrapper">
              <transition name="search">
                <input 
                  v-if="searchOpen" 
                  type="text" 
                  class="search-input" 
                  placeholder="Szukaj..." 
                />
              </transition>

              <button class="search-btn" @click="toggleSearch" aria-label="Szukaj">
                <img src="../assets/icons/search.png" alt="Szukaj" />
              </button>
            </div>

            <button 
              class="hamburger-btn" 
              :class="{ 'is-active': mobileMenuOpen }" 
              @click="toggleMobileMenu"
              aria-label="Menu"
            >
              <span></span>
              <span></span>
              <span></span>
            </button>
          </div>
          
        </div>
      </nav>
    </div>
  </header>
</template>

<style scoped>
.navbar-wrapper {
  position: relative;
  height: 72px;
  background: #fff;
  border-bottom: 1px solid #ececec;
  z-index: 1000;
}

.navbar-content {
  height: 72px;
  display: flex;
  justify-content: space-between;
  align-items: center;
}

.logo img {
  width: 114px;
  display: block;
}

.right-side {
  display: flex;
  align-items: center;
  gap: 32px;
}

.nav-menu {
  display: flex;
  align-items: center;
}

.nav-list {
  display: flex;
  align-items: center;
  gap: 48px;
  margin: 0;
  padding: 0;
  list-style: none;
}

.nav-list a {
  color: #111;
  text-decoration: none;
  font-family: 'Inter', sans-serif;
  font-size: 14px;
  transition: 0.25s;
}

.nav-list a:hover {
  color: #1f6d38;
}

.dropdown-custom {
  position: relative;
}

.nav-button {
  background: none;
  border: none;
  display: flex;
  align-items: center;
  gap: 6px;
  font-family: 'Inter', sans-serif;
  font-size: 14px;
  color: #111;
  cursor: pointer;
  padding: 0;
}

.arrow {
  font-size: 10px;
  transition: transform 0.25s ease;
}

.arrow.rotate {
  transform: rotate(180deg);
}

.dropdown-box {
  position: absolute;
  top: 42px;
  left: 0;
  width: 190px;
  background: #fff;
  border-radius: 12px;
  box-shadow: 0 10px 25px rgba(0, 0, 0, 0.12);
  display: flex;
  flex-direction: column;
  overflow: hidden;
  z-index: 1000;
}

.dropdown-box a {
  padding: 14px 18px;
  color: #111;
}

.dropdown-box a:hover {
  background: #f5f5f5;
}

.nav-actions {
  display: flex;
  align-items: center;
  gap: 16px;
}

.search-wrapper {
  display: flex;
  align-items: center;
  position: relative;
}

.search-btn {
  background: none;
  border: none;
  cursor: pointer;
  padding: 0;
  display: flex;
  align-items: center;
}

.search-btn img {
  width: 20px;
  height: 20px;
}

.search-input {
  width: 220px;
  height: 40px;
  border: 1px solid #d8d8d8;
  border-radius: 20px;
  padding: 0 16px;
  outline: none;
  font-size: 14px;
  margin-right: 10px;
}

.hamburger-btn {
  display: none;
  flex-direction: column;
  justify-content: space-between;
  width: 24px;
  height: 18px;
  background: transparent;
  border: none;
  cursor: pointer;
  padding: 0;
  z-index: 1001;
}

.hamburger-btn span {
  width: 100%;
  height: 2px;
  background-color: #111;
  border-radius: 2px;
  transition: all 0.3s ease;
}

.hamburger-btn.is-active span:nth-child(1) {
  transform: translateY(8px) rotate(45deg);
}

.hamburger-btn.is-active span:nth-child(2) {
  opacity: 0;
}

.hamburger-btn.is-active span:nth-child(3) {
  transform: translateY(-8px) rotate(-45deg);
}

.search-enter-active,
.search-leave-active {
  transition: all 0.3s ease;
}

.search-enter-from,
.search-leave-to {
  width: 0;
  opacity: 0;
  padding: 0;
  margin-right: 0;
}

.dropdown-enter-active,
.dropdown-leave-active {
  transition: all 0.2s ease;
}

.dropdown-enter-from,
.dropdown-leave-to {
  opacity: 0;
  transform: translateY(-10px);
}

@media (max-width: 991px) {
  .hamburger-btn {
    display: flex;
  }

  .nav-menu {
    position: absolute;
    top: 72px;
    left: 0;
    width: 100%;
    background: #ffffff;
    border-bottom: 1px solid #ececec;
    box-shadow: 0 10px 20px rgba(0, 0, 0, 0.05);
    padding: 24px 0;
    flex-direction: column;
    align-items: flex-start;
    display: none;
  }

  .nav-menu.is-open {
    display: flex;
  }

  .nav-list {
    flex-direction: column;
    align-items: flex-start;
    width: 100%;
    gap: 0;
  }

  .nav-list li {
    width: 100%;
  }

  .nav-list a,
  .nav-button {
    display: flex;
    justify-content: space-between;
    width: 100%;
    padding: 14px 24px;
    font-size: 16px;
    box-sizing: border-box;
  }

  .dropdown-box {
    position: static;
    width: 100%;
    box-shadow: none;
    border-radius: 0;
    background: #f9f9f9;
    padding-left: 16px;
  }

  .dropdown-box a {
    padding: 12px 24px;
    font-size: 15px;
    color: #444;
  }

  .search-input {
    position: absolute;
    right: 35px;
    top: -8px;
    width: 180px;
    background: #fff;
  }
}

@media (max-width: 576px) {
  .search-input {
    width: 140px;
  }
}
</style>