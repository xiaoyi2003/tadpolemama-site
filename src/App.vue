<template>
  <NavBar />
  <div class="main-content">
    <router-view />
  </div>
</template>

<script setup>
import NavBar from './components/NavBar.vue'
</script>

<style>
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

body {
  font-family: 'Helvetica Neue', Helvetica, 'PingFang SC', 'Hiragino Sans GB', 'Microsoft YaHei', '微软雅黑', Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #333;
  line-height: 1.5;
}

.main-content {
  padding-top: 80px; /* 与导航栏高度相同，确保内容不被导航栏遮挡 */
}

.container {
  max-width: 1200px;
  margin: 0 auto;
  padding: 0 20px;
}

.section {
  padding: 60px 0;
}

.section-title {
  text-align: center;
  margin-bottom: 40px;
  font-size: 32px;
  font-weight: bold;
  color: #333;
}

.section-subtitle {
  text-align: center;
  margin-bottom: 30px;
  font-size: 18px;
  color: #666;
  max-width: 700px;
  margin-left: auto;
  margin-right: auto;
}
</style>
