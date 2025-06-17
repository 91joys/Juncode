<template>
  <nav class="navbar">
    <div class="nav-container">
      <!-- Logo 區域 -->
      <div class="nav-logo">
        <NuxtLink to="/" class="logo-link">
          <span class="logo-text">JunCode</span>
        </NuxtLink>
      </div>

      <!-- 導航選單 -->
      <ul class="nav-menu">
        <li class="nav-item">
          <NuxtLink to="/" class="nav-link">
            <i class="icon">🏠</i>
            <span>首頁</span>
          </NuxtLink>
        </li>
        <li class="nav-item">
          <NuxtLink to="/about" class="nav-link">
            <i class="icon">👨‍💻</i>
            <span>關於我</span>
          </NuxtLink>
        </li>
        <li class="nav-item">
          <NuxtLink to="/works" class="nav-link">
            <i class="icon">💼</i>
            <span>我的作品</span>
          </NuxtLink>
        </li>
      </ul>

      <!-- 漢堡選單按鈕 (手機版) -->
      <div
        class="hamburger"
        @click="toggleMenu"
        :class="{ active: isMenuOpen }"
      >
        <span></span>
        <span></span>
        <span></span>
      </div>
    </div>
  </nav>
</template>

<script setup>
import { ref } from "vue";

const isMenuOpen = ref(false);

const toggleMenu = () => {
  isMenuOpen.value = !isMenuOpen.value;
};
</script>

<style scoped>
.navbar {
  background: rgba(255, 255, 255, 0.1);
  backdrop-filter: blur(20px);
  border-bottom: 1px solid rgba(255, 255, 255, 0.2);
  position: sticky;
  top: 0;
  z-index: 1000;
  box-shadow: 0 8px 32px rgba(0, 0, 0, 0.1);
}

.nav-container {
  max-width: 1200px;
  margin: 0 auto;
  padding: 0 2rem;
  display: flex;
  justify-content: space-between;
  align-items: center;
  height: 70px;
}

/* Logo 樣式 */
.nav-logo {
  font-size: 1.5rem;
  font-weight: bold;
}

.logo-link {
  text-decoration: none;
  color: white;
  transition: all 0.3s ease;
}

.logo-text {
  background: linear-gradient(45deg, #fff, #e2e8f0);
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
  background-clip: text;
  font-weight: 800;
  letter-spacing: -0.5px;
}

.logo-link:hover .logo-text {
  background: linear-gradient(45deg, #ffd700, #ffed4e);
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
  background-clip: text;
  transform: scale(1.05);
}

/* 導航選單 */
.nav-menu {
  display: flex;
  list-style: none;
  gap: 2rem;
  margin: 0;
  padding: 0;
}

.nav-item {
  position: relative;
}

.nav-link {
  display: flex;
  align-items: center;
  gap: 0.5rem;
  text-decoration: none;
  color: rgba(255, 255, 255, 0.9);
  padding: 0.75rem 1.5rem;
  border-radius: 50px;
  font-weight: 500;
  transition: all 0.3s ease;
  position: relative;
  overflow: hidden;
}

.nav-link::before {
  content: "";
  position: absolute;
  top: 0;
  left: -100%;
  width: 100%;
  height: 100%;
  background: linear-gradient(
    45deg,
    rgba(255, 255, 255, 0.1),
    rgba(255, 255, 255, 0.2)
  );
  transition: left 0.3s ease;
  z-index: -1;
}

.nav-link:hover::before {
  left: 0;
}

.nav-link:hover {
  color: white;
  transform: translateY(-2px);
  box-shadow: 0 10px 25px rgba(0, 0, 0, 0.2);
}

.nav-link.router-link-active {
  background: rgba(255, 255, 255, 0.2);
  color: white;
  box-shadow: 0 4px 15px rgba(0, 0, 0, 0.1);
}

.icon {
  font-size: 1.1rem;
}

/* 漢堡選單 */
.hamburger {
  display: none;
  flex-direction: column;
  cursor: pointer;
  width: 24px;
  height: 24px;
  justify-content: space-around;
}

.hamburger span {
  width: 100%;
  height: 2px;
  background: white;
  border-radius: 2px;
  transition: all 0.3s ease;
}

.hamburger.active span:nth-child(1) {
  transform: rotate(45deg) translate(5px, 5px);
}

.hamburger.active span:nth-child(2) {
  opacity: 0;
}

.hamburger.active span:nth-child(3) {
  transform: rotate(-45deg) translate(7px, -6px);
}

/* 響應式設計 */
@media (max-width: 768px) {
  .nav-container {
    padding: 0 1rem;
  }

  .nav-menu {
    position: fixed;
    top: 70px;
    left: 0;
    width: 100%;
    height: calc(100vh - 70px);
    background: rgba(0, 0, 0, 0.9);
    backdrop-filter: blur(20px);
    flex-direction: column;
    justify-content: flex-start;
    align-items: center;
    padding-top: 2rem;
    gap: 1rem;
    transform: translateX(-100%);
    transition: transform 0.3s ease;
  }

  .nav-menu.active {
    transform: translateX(0);
  }

  .hamburger {
    display: flex;
  }

  .nav-link {
    width: 200px;
    justify-content: center;
    font-size: 1.1rem;
  }
}

/* 動畫效果 */
@keyframes fadeInUp {
  from {
    opacity: 0;
    transform: translateY(20px);
  }
  to {
    opacity: 1;
    transform: translateY(0);
  }
}

.nav-item {
  animation: fadeInUp 0.6s ease forwards;
}

.nav-item:nth-child(1) {
  animation-delay: 0.1s;
}
.nav-item:nth-child(2) {
  animation-delay: 0.2s;
}
.nav-item:nth-child(3) {
  animation-delay: 0.3s;
}
</style>
