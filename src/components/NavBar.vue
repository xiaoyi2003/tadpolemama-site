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
          <h1 class="logo-text">默默文化传媒</h1>
        </router-link>
        <div class="menu-toggle" @click="toggleMenu" v-if="isMobile">
          <i :class="isMenuOpen ? 'fas fa-times' : 'fas fa-bars'"></i>
        </div>
      </div>
      <div class="menu-items" :class="{ 'mobile': isMobile, 'open': isMenuOpen }">
        <el-menu-item index="/">首页</el-menu-item>
        <el-menu-item index="/about">关于我们</el-menu-item>
        <el-menu-item index="/services">服务内容</el-menu-item>
        <el-menu-item index="/cases">案例展示</el-menu-item>
        <el-menu-item index="/talents">艺人资源</el-menu-item>
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
  }

  .menu-items {
    display: none;
    width: 100%;
    flex-direction: column;
  }

  .menu-items.mobile {
    display: flex;
  }

  .menu-items.mobile.open {
    display: flex;
  }

  .menu-items .el-menu-item {
    margin-left: 0;
    width: 100%;
    text-align: left;
  }
}
</style>