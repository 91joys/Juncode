<template>
  <div class="my-works">
    <div class="works-container">
      <!-- 標題區域 -->
      <div class="works-header">
        <h1 class="works-title">
          <span class="title-gradient">我的作品集</span>
        </h1>
        <div class="title-underline"></div>
        <p class="works-subtitle">這裡展示了我精心製作的一些項目</p>
      </div>

      <!-- 作品網格 -->
      <div class="works-grid">
        <div
          v-for="(work, index) in works"
          :key="work.id"
          class="work-card"
          :style="{ 'animation-delay': `${index * 0.2}s` }"
        >
          <div class="card-header">
            <div class="work-icon">
              <img
                v-if="work.icon.includes('png')"
                :src="work.icon"
                :alt="work.title"
                class="icon-image"
              />
              <span v-else>{{ work.icon }}</span>
            </div>
            <div class="work-number">#{{ index + 1 }}</div>
          </div>

          <div class="card-content">
            <h2 class="work-title">{{ work.title }}</h2>
            <p class="work-description">{{ work.description }}</p>

            <div class="work-tags">
              <span v-for="tag in work.tags" :key="tag" class="work-tag">{{
                tag
              }}</span>
            </div>
          </div>

          <div class="card-footer">
            <a
              :href="work.websiteUrl"
              target="_blank"
              class="work-link website-link"
            >
              <span class="link-icon">🌐</span>
              訪問網站
            </a>
          </div>

          <div class="card-glow"></div>
        </div>
      </div>

      <!-- 更多作品按鈕 -->
      <div class="more-works">
        <button class="more-btn">
          <span>查看更多作品</span>
          <span class="btn-icon">🚀</span>
        </button>
      </div>
    </div>
  </div>
</template>

<script setup>
import { ref } from "vue";

const works = ref([
  {
    id: 1,
    title: "MLB 道奇資訊網",
    description:
      "使用 Vue 3 構建的 MLB 中文資訊平台，聚焦道奇隊，提供球員介紹與現代化網頁設計體驗。",
    icon: "/webicon.png",
    websiteUrl: "https://mlb-web-gilt.vercel.app/",
    tags: ["Vue.js", "Figma", "CSS", "Javascript", "Vercel"],
  },
  {
    id: 2,
    title: "課堂練習",
    description:
      "課堂時使用 HTML、CSS 和 JavaScript 製作的網頁練習，並透過 GitHub Pages 部署。",
    icon: "💻",
    websiteUrl: "https://jyw-learning.github.io/basic-91joys/",
    tags: ["HTML", "CSS", "Javascript", "GitHub Pages"],
  },
  {
    id: 3,
    title: "天氣預報應用(模擬)",
    description:
      "即時天氣數據顯示應用，支援多城市查詢、天氣預警和美觀的視覺化界面。",
    icon: "🌤️",
    websiteUrl: "https://example-weather.com",
    tags: ["JavaScript", "API", "Chart.js"],
  },
  {
    id: 4,
    title: "任務管理系統(模擬)",
    description:
      "團隊協作的任務管理工具，支援項目追蹤、團隊溝通和進度管理功能。",
    icon: "📋",
    websiteUrl: "https://example-tasks.com",
    tags: ["TypeScript", "Express", "Socket.io"],
  },
  {
    id: 5,
    title: "數據視覺化儀表板(模擬)",
    description: "互動式數據分析平台，提供多種圖表類型和即時數據更新功能。",
    icon: "📊",
    websiteUrl: "https://example-dashboard.com",
    tags: ["D3.js", "Python", "Flask"],
  },
  {
    id: 6,
    title: "社交媒體應用(模擬)",
    description:
      "現代化的社交平台，包含用戶認證、貼文分享、即時通訊和通知系統。",
    icon: "📱",
    websiteUrl: "https://example-social.com",
    tags: ["React Native", "Firebase", "Redux"],
  },
  {
    id: 7,
    title: "電子商務平台(模擬)",
    description:
      "全功能的電商網站，包含商品管理、購物車、訂單處理和支付系統整合。",
    icon: "🛒",
    websiteUrl: "https://example-ecommerce.com",
    tags: ["React", "Node.js", "MongoDB"],
  },
]);
</script>

<style scoped>
.my-works {
  min-height: calc(100vh - 70px);
  padding: 2rem;
  background: transparent;
}

.works-container {
  max-width: 1400px;
  margin: 0 auto;
}

/* 標題區域 */
.works-header {
  text-align: center;
  margin-bottom: 4rem;
}

.works-title {
  font-size: 3rem;
  font-weight: 800;
  margin-bottom: 1rem;
}

.title-gradient {
  background: linear-gradient(45deg, #fff, #e2e8f0);
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
  background-clip: text;
}

.title-underline {
  width: 120px;
  height: 4px;
  background: linear-gradient(45deg, #667eea, #764ba2);
  margin: 0 auto 1.5rem;
  border-radius: 2px;
}

.works-subtitle {
  font-size: 1.2rem;
  color: rgba(255, 255, 255, 0.8);
  margin: 0;
}

/* 作品網格 */
.works-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(350px, 1fr));
  gap: 2rem;
  margin-bottom: 3rem;
}

.work-card {
  background: rgba(255, 255, 255, 0.1);
  backdrop-filter: blur(20px);
  border: 1px solid rgba(255, 255, 255, 0.2);
  border-radius: 20px;
  padding: 2rem;
  transition: all 0.3s ease;
  position: relative;
  overflow: hidden;
  opacity: 0;
  transform: translateY(30px);
  animation: fadeInUp 0.8s ease forwards;
}

.work-card::before {
  content: "";
  position: absolute;
  top: 0;
  left: -100%;
  width: 100%;
  height: 100%;
  background: linear-gradient(
    90deg,
    transparent,
    rgba(255, 255, 255, 0.1),
    transparent
  );
  transition: left 0.5s ease;
}

.work-card:hover::before {
  left: 100%;
}

.work-card:hover {
  transform: translateY(-10px);
  box-shadow: 0 25px 50px rgba(0, 0, 0, 0.3);
  border-color: rgba(255, 255, 255, 0.3);
}

.card-glow {
  position: absolute;
  top: -2px;
  left: -2px;
  right: -2px;
  bottom: -2px;
  background: linear-gradient(45deg, #667eea, #764ba2, #667eea);
  border-radius: 20px;
  filter: blur(10px);
  opacity: 0;
  transition: opacity 0.3s ease;
  z-index: -1;
}

.work-card:hover .card-glow {
  opacity: 0.2;
}

/* 卡片標題 */
.card-header {
  display: flex;
  justify-content: space-between;
  align-items: center;
  margin-bottom: 1.5rem;
}

.work-icon {
  font-size: 2.5rem;
}

.work-number {
  background: rgba(255, 255, 255, 0.2);
  color: white;
  padding: 0.3rem 0.8rem;
  border-radius: 15px;
  font-size: 0.9rem;
  font-weight: 600;
}

/* 卡片內容 */
.card-content {
  margin-bottom: 2rem;
}

.work-title {
  color: white;
  font-size: 1.4rem;
  font-weight: 700;
  margin-bottom: 1rem;
  line-height: 1.3;
}

.work-description {
  color: rgba(255, 255, 255, 0.9);
  line-height: 1.6;
  margin-bottom: 1.5rem;
  font-size: 0.95rem;
}

.work-tags {
  display: flex;
  flex-wrap: wrap;
  gap: 0.5rem;
}

.work-tag {
  background: rgba(255, 255, 255, 0.15);
  color: white;
  padding: 0.3rem 0.8rem;
  border-radius: 15px;
  font-size: 0.8rem;
  font-weight: 500;
  border: 1px solid rgba(255, 255, 255, 0.2);
}

/* 卡片底部 */
.card-footer {
  display: flex;
  gap: 1rem;
}

.work-link {
  display: flex;
  align-items: center;
  gap: 0.5rem;
  color: white;
  text-decoration: none;
  background: rgba(255, 255, 255, 0.1);
  padding: 0.8rem 1.2rem;
  border-radius: 25px;
  border: 1px solid rgba(255, 255, 255, 0.2);
  transition: all 0.3s ease;
  font-weight: 500;
  font-size: 0.9rem;
  flex: 1;
  justify-content: center;
  width: 100%; /* 讓按鈕佔滿整個寬度 */
}

.website-link:hover {
  background: rgba(118, 75, 162, 0.3);
  border-color: rgba(118, 75, 162, 0.5);
  transform: translateY(-2px);
  box-shadow: 0 8px 20px rgba(118, 75, 162, 0.3);
}

.link-icon {
  font-size: 1rem;
}

/* 更多作品按鈕 */
.more-works {
  text-align: center;
  margin-top: 3rem;
}

.more-btn {
  background: rgba(255, 255, 255, 0.1);
  color: white;
  border: 2px solid rgba(255, 255, 255, 0.3);
  padding: 1rem 2rem;
  border-radius: 50px;
  font-size: 1.1rem;
  font-weight: 600;
  cursor: pointer;
  transition: all 0.3s ease;
  display: inline-flex;
  align-items: center;
  gap: 0.5rem;
}

.more-btn:hover {
  background: rgba(255, 255, 255, 0.2);
  transform: translateY(-3px);
  box-shadow: 0 15px 30px rgba(0, 0, 0, 0.2);
}

.btn-icon {
  transition: transform 0.3s ease;
}

.more-btn:hover .btn-icon {
  transform: translateX(5px);
}

/* 響應式設計 */
@media (max-width: 768px) {
  .my-works {
    padding: 1rem;
  }

  .works-title {
    font-size: 2rem;
  }

  .works-grid {
    grid-template-columns: 1fr;
    gap: 1.5rem;
  }

  .work-card {
    padding: 1.5rem;
  }

  .work-link {
    justify-content: center;
  }
}

@media (max-width: 480px) {
  .works-header {
    margin-bottom: 2rem;
  }

  .work-card {
    padding: 1rem;
  }

  .work-title {
    font-size: 1.2rem;
  }
}

/* 動畫 */
@keyframes fadeInUp {
  to {
    opacity: 1;
    transform: translateY(0);
  }
}

/* 卡片進入動畫延遲 */
.work-card:nth-child(1) {
  animation-delay: 0.1s;
}
.work-card:nth-child(2) {
  animation-delay: 0.2s;
}
.work-card:nth-child(3) {
  animation-delay: 0.3s;
}
.work-card:nth-child(4) {
  animation-delay: 0.4s;
}
.work-card:nth-child(5) {
  animation-delay: 0.5s;
}
.work-card:nth-child(6) {
  animation-delay: 0.6s;
}

/* 圖片圖標樣式 */
.icon-image {
  width: 40px;
  height: 40px;
  object-fit: contain;
  border-radius: 8px;
}
</style>
