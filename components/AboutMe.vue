<template>
  <div class="about-me">
    <div class="about-container">
      <!-- 個人照片區域 -->
      <div class="profile-section">
        <div class="profile-image">
          <div class="image-placeholder">
            <img src="/me.png" alt="Jun的照片" class="profile-photo" />
          </div>
          <div class="image-glow"></div>
        </div>

        <!-- 個人資訊 -->
        <div class="profile-info">
          <h2 class="profile-name">Jun</h2>
          <div class="profile-details">
            <div class="detail-item">
              <span class="detail-icon">🎓</span>
              <span class="detail-text">中原大學電機系</span>
            </div>
            <div class="detail-item">
              <span class="detail-icon">⚾</span>
              <span class="detail-text">喜歡看棒球是個棒球迷</span>
            </div>
          </div>
        </div>
      </div>

      <!-- 內容區域 -->
      <div class="content-section">
        <div class="intro-header">
          <h1 class="main-title">
            <span class="title-gradient">關於我</span>
          </h1>
          <div class="title-underline"></div>
        </div>

        <div class="intro-content">
          <div class="intro-card">
            <div class="card-icon">🚀</div>
            <h3>熱情的開發者</h3>
            <p>{{ introduction }}</p>
          </div>

          <div class="intro-card">
            <div class="card-icon">💡</div>
            <h3>持續學習</h3>
            <p>
              我喜歡創建美觀且功能強大的應用程式，並不斷學習新技術以提升自己的技能。
            </p>
          </div>

          <div class="intro-card">
            <div class="card-icon">🎯</div>
            <h3>興趣愛好</h3>
            <p>在我的空閒時間，我喜歡：</p>
            <ul class="hobbies-list">
              <li v-for="hobby in hobbies" :key="hobby" class="hobby-item">
                <span class="hobby-icon">✨</span>
                {{ hobby }}
              </li>
            </ul>
          </div>
        </div>

        <!-- 技能標籤 -->
        <div class="skills-section">
          <h3 class="skills-title">技術領域</h3>
          <div class="skills-tags">
            <span v-for="skill in skills" :key="skill" class="skill-tag">
              {{ skill }}
            </span>
          </div>
        </div>

        <!-- 聯絡方式 -->
        <div class="contact-section">
          <h3 class="contact-title">聯絡我</h3>
          <div class="contact-links">
            <a href="#" class="contact-link">
              <span class="contact-icon">📧</span>
              Email
            </a>
            <a href="#" class="contact-link">
              <span class="contact-icon">💼</span>
              LinkedIn
            </a>
            <a href="https://github.com/91joys" class="contact-link">
              <span class="contact-icon">🐙</span>
              GitHub
            </a>
            <a href="https://www.instagram.com/91.joys/" class="contact-link">
              <span class="contact-icon">🌐</span>
              IG
            </a>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
import { ref } from "vue";

const introduction = ref("您好！我是一名熱愛編程的開發者，專注於前端技術。");
const hobbies = ref([
  "閱讀技術文章",
  "旅行探索",
  "探索新的技術趨勢",
  "攝影記錄生活",
  "看棒球",
]);
const skills = ref([
  "Vue.js",
  "Nuxt.js",
  "JavaScript",
  "HTML",
  "CSS",
  "Node.js",
  "Git",
  "Figma",
]);
</script>

<style scoped>
.about-me {
  min-height: calc(100vh - 70px);
  padding: 2rem;
  background: transparent;
}

.about-container {
  max-width: 1200px;
  margin: 0 auto;
  display: grid;
  grid-template-columns: 1fr 2fr;
  gap: 3rem;
  align-items: start;
}

/* 個人照片區域 */
.profile-section {
  display: flex;
  flex-direction: column;
  align-items: center;
  position: sticky;
  top: 100px;
}

.profile-image {
  position: relative;
  width: 250px;
  height: 250px;
  margin-bottom: 2rem;
}

.image-placeholder {
  width: 100%;
  height: 100%;
  background: linear-gradient(
    135deg,
    rgba(255, 255, 255, 0.2),
    rgba(255, 255, 255, 0.1)
  );
  border-radius: 50%;
  display: flex;
  align-items: center;
  justify-content: center;
  backdrop-filter: blur(20px);
  border: 2px solid rgba(255, 255, 255, 0.3);
  position: relative;
  z-index: 2;
  overflow: hidden;
}

.profile-photo {
  width: 100%;
  height: 100%;
  object-fit: cover;
  border-radius: 50%;
}

/* 個人資訊 */
.profile-info {
  text-align: center;
  color: white;
}

.profile-name {
  font-size: 2rem;
  font-weight: 700;
  margin-bottom: 1.5rem;
  background: linear-gradient(45deg, #fff, #e2e8f0);
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
  background-clip: text;
}

.profile-details {
  display: flex;
  flex-direction: column;
  gap: 1rem;
}

.detail-item {
  display: flex;
  align-items: center;
  gap: 0.75rem;
  background: rgba(255, 255, 255, 0.1);
  backdrop-filter: blur(20px);
  border: 1px solid rgba(255, 255, 255, 0.2);
  border-radius: 15px;
  padding: 1rem 1.5rem;
  transition: all 0.3s ease;
}

.detail-item:hover {
  background: rgba(255, 255, 255, 0.15);
  transform: translateY(-2px);
  box-shadow: 0 8px 20px rgba(0, 0, 0, 0.2);
}

.detail-icon {
  font-size: 1.2rem;
  flex-shrink: 0;
}

.detail-text {
  font-size: 0.95rem;
  color: rgba(255, 255, 255, 0.9);
  font-weight: 500;
}

/* 內容區域 */
.content-section {
  margin-top: 2rem;
}

.intro-header {
  text-align: center;
  margin-bottom: 3rem;
}

.main-title {
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
  width: 100px;
  height: 4px;
  background: linear-gradient(45deg, #667eea, #764ba2);
  margin: 0 auto;
  border-radius: 2px;
}

/* 介紹卡片 */
.intro-content {
  display: flex;
  flex-direction: column;
  gap: 2rem;
  margin-bottom: 3rem;
}

.intro-card {
  background: rgba(255, 255, 255, 0.1);
  backdrop-filter: blur(20px);
  border: 1px solid rgba(255, 255, 255, 0.2);
  border-radius: 20px;
  padding: 2rem;
  transition: all 0.3s ease;
  position: relative;
  overflow: hidden;
}

.intro-card::before {
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

.intro-card:hover::before {
  left: 100%;
}

.intro-card:hover {
  transform: translateY(-5px);
  box-shadow: 0 20px 40px rgba(0, 0, 0, 0.2);
  border-color: rgba(255, 255, 255, 0.3);
}

.card-icon {
  font-size: 2rem;
  margin-bottom: 1rem;
}

.intro-card h3 {
  color: white;
  font-size: 1.3rem;
  font-weight: 600;
  margin-bottom: 1rem;
}

.intro-card p {
  color: rgba(255, 255, 255, 0.9);
  line-height: 1.6;
  margin-bottom: 1rem;
}

/* 興趣列表 */
.hobbies-list {
  list-style: none;
  padding: 0;
  margin: 1rem 0 0 0;
}

.hobby-item {
  display: flex;
  align-items: center;
  gap: 0.5rem;
  color: rgba(255, 255, 255, 0.9);
  margin-bottom: 0.5rem;
  font-size: 0.95rem;
}

.hobby-icon {
  color: #ffd700;
}

/* 技能區域 */
.skills-section {
  margin-bottom: 3rem;
}

.skills-title {
  color: white;
  font-size: 1.3rem;
  font-weight: 600;
  margin-bottom: 1rem;
  text-align: center;
}

.skills-tags {
  display: flex;
  flex-wrap: wrap;
  gap: 1rem;
  justify-content: center;
}

.skill-tag {
  background: rgba(255, 255, 255, 0.1);
  color: white;
  padding: 0.5rem 1rem;
  border-radius: 25px;
  font-size: 0.9rem;
  font-weight: 500;
  border: 1px solid rgba(255, 255, 255, 0.2);
  transition: all 0.3s ease;
}

.skill-tag:hover {
  background: rgba(255, 255, 255, 0.2);
  transform: translateY(-2px);
  box-shadow: 0 5px 15px rgba(0, 0, 0, 0.2);
}

/* 聯絡區域 */
.contact-section {
  text-align: center;
}

.contact-title {
  color: white;
  font-size: 1.3rem;
  font-weight: 600;
  margin-bottom: 1.5rem;
}

.contact-links {
  display: flex;
  gap: 1rem;
  justify-content: center;
  flex-wrap: wrap;
}

.contact-link {
  display: flex;
  align-items: center;
  gap: 0.5rem;
  color: white;
  text-decoration: none;
  background: rgba(255, 255, 255, 0.1);
  padding: 0.75rem 1.5rem;
  border-radius: 25px;
  border: 1px solid rgba(255, 255, 255, 0.2);
  transition: all 0.3s ease;
  font-weight: 500;
}

.contact-link:hover {
  background: rgba(255, 255, 255, 0.2);
  transform: translateY(-2px);
  box-shadow: 0 10px 25px rgba(0, 0, 0, 0.2);
}

.contact-icon {
  font-size: 1.1rem;
}

/* 響應式設計 */
@media (max-width: 968px) {
  .about-container {
    grid-template-columns: 1fr;
    gap: 2rem;
  }

  .profile-section {
    position: static;
  }

  .profile-image {
    width: 200px;
    height: 200px;
    margin-bottom: 1.5rem;
  }

  .profile-name {
    font-size: 1.5rem;
  }

  .detail-item {
    padding: 0.75rem 1rem;
  }
}

@media (max-width: 768px) {
  .about-me {
    padding: 1rem;
  }

  .main-title {
    font-size: 2rem;
  }

  .intro-card {
    padding: 1.5rem;
  }

  .contact-links {
    flex-direction: column;
    align-items: center;
  }

  .contact-link {
    width: 200px;
    justify-content: center;
  }
}

/* 進入動畫 */
.intro-card {
  animation: fadeInUp 0.8s ease forwards;
}

.intro-card:nth-child(1) {
  animation-delay: 0.2s;
}
.intro-card:nth-child(2) {
  animation-delay: 0.4s;
}
.intro-card:nth-child(3) {
  animation-delay: 0.6s;
}

@keyframes fadeInUp {
  from {
    opacity: 0;
    transform: translateY(30px);
  }
  to {
    opacity: 1;
    transform: translateY(0);
  }
}
</style>
