<template>
  <div>
    <NuxtLayout>
      <NuxtPage />
    </NuxtLayout>
  </div>
</template>

<script setup>
// 使用 Composition API
// 可以在這裡添加全域的邏輯或狀態管理
</script>

<style>
/* 全域樣式 */
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

body {
  font-family: "Inter", "Segoe UI", "Roboto", sans-serif;
  line-height: 1.6;
  color: #2d3748;
  background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
  min-height: 100vh;
  overflow-x: hidden;
}

html {
  scroll-behavior: smooth;
}

/* 美化滾動條 */
::-webkit-scrollbar {
  width: 8px;
}

::-webkit-scrollbar-track {
  background: #f1f1f1;
  border-radius: 4px;
}

::-webkit-scrollbar-thumb {
  background: linear-gradient(45deg, #667eea, #764ba2);
  border-radius: 4px;
}

::-webkit-scrollbar-thumb:hover {
  background: linear-gradient(45deg, #5a67d8, #6b46c1);
}

/* 全域動畫 */
* {
  transition: all 0.3s ease;
}

/* 選取文字的顏色 */
::selection {
  background: rgba(102, 126, 234, 0.3);
  color: #2d3748;
}

/* 響應式字體大小 */
@media (max-width: 768px) {
  body {
    font-size: 14px;
  }
}

@media (min-width: 1200px) {
  body {
    font-size: 16px;
  }
}

/* 載入動畫 */
.page-enter-active,
.page-leave-active {
  transition: all 0.4s ease-in-out;
}

.page-enter-from,
.page-leave-to {
  opacity: 0;
  transform: translateY(20px);
}
</style>
