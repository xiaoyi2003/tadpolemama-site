<template>
  <div class="navbar-container">
    <el-menu
      :default-active="activeIndex"
      class="navbar"
      :mode="isMobile ? 'vertical' : 'horizontal'"
      router
      @select="handleSelect"
      :collapse="isMobile && !isMenuOpen"
    >
      <div class="logo-container">
        <router-link to="/">
          <h1 class="logo-text">Tadpolemama 母婴</h1>
        </router-link>
        <div class="menu-toggle" @click="toggleMenu" v-if="isMobile">
          <i :class="isMenuOpen ? 'fas fa-times' : 'fas fa-bars'"></i>
        </div>
      </div>
      <div class="menu-items" :class="{ 'mobile': isMobile, 'open': isMenuOpen }">
        <el-menu-item index="/">首页</el-menu-item>
        <el-menu-item index="/about">关于我们</el-menu-item>
        <el-menu-item index="/services">Tadpolemama月子中心</el-menu-item>
        <el-menu-item index="/cases">案例展示</el-menu-item>
        <el-menu-item index="/talents">Tadpole doula月嫂平台</el-menu-item>
        <el-menu-item index="/contact">联系我们</el-menu-item>
      </div>
    </el-menu>
  </div>
</template>

<script setup>
import { ref, computed, onMounted, onUnmounted } from 'vue'
import { useRoute } from 'vue-router'

const route = useRoute()
const activeIndex = computed(() => route.path)
const isMobile = ref(false)
const isMenuOpen = ref(false)

const handleSelect = (key) => {
  if (isMobile.value) {
    isMenuOpen.value = false
  }
}

const toggleMenu = () => {
  isMenuOpen.value = !isMenuOpen.value
}

const checkMobile = () => {
  isMobile.value = window.innerWidth <= 768
  if (!isMobile.value) {
    isMenuOpen.value = false
  }
}

onMounted(() => {
  checkMobile()
  window.addEventListener('resize', checkMobile)
})

onUnmounted(() => {
  window.removeEventListener('resize', checkMobile)
})
</script>

<style scoped>
.navbar-container {
  position: sticky;
  top: 0;
  z-index: 1000;
  box-shadow: 0 2px 12px 0 rgba(0, 0, 0, 0.1);
  background-color: #fff;
}

.navbar {
  display: flex;
  align-items: center;
  height: 80px;
  max-width: 1200px;
  margin: 0 auto;
  padding: 0 20px;
  background-color: #fff;
  width: 100%;
}

.logo-container {
  margin-right: 40px;
  display: flex;
  align-items: center;
}

.logo-container a {
  text-decoration: none;
}

.logo-text {
  color: #409EFF;
  margin: 0;
  font-size: 24px;
  font-weight: bold;
}

.menu-items {
  display: flex;
  align-items: center;
  justify-content: flex-end;
}

.menu-items .el-menu-item {
  margin-left: 5px;
}

@media (max-width: 768px) {
  .navbar {
    flex-direction: column;
    height: auto;
    padding: 0;
    position: relative;
  }

  .logo-container {
    width: 100%;
    padding: 15px 20px;
    justify-content: space-between;
    margin-right: 0;
  }

  .menu-toggle {
    display: flex;
    align-items: center;
    font-size: 24px;
    color: #409EFF;
    cursor: pointer;
    z-index: 1001;
  }

  .menu-items {
    display: none;
    position: fixed;
    top: 0;
    right: -250px;
    width: 250px;
    height: 100vh;
    background-color: #fff;
    flex-direction: column;
    box-shadow: -2px 0 10px rgba(0, 0, 0, 0.1);
    transition: right 0.3s ease;
    padding-top: 80px;
    z-index: 999;
  }

  .menu-items.mobile {
    display: flex;
  }

  .menu-items.mobile.open {
    display: flex;
    right: 0;
  }

  .menu-items .el-menu-item {
    margin-left: 0;
    width: 100%;
    text-align: left;
    border-bottom: 1px solid #f0f0f0;
  }
}
</style>