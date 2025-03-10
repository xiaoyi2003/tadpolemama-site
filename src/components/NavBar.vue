<template>
  <div class="navbar-container">
    <el-menu
      :default-active="activeIndex"
      class="navbar"
      mode="horizontal"
      router
      @select="handleSelect"
    >
      <div class="logo-container">
        <router-link to="/">
          <h1 class="logo-text">默默文化传媒</h1>
        </router-link>
      </div>
      <div class="menu-items">
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
import { ref, computed } from 'vue'
import { useRoute } from 'vue-router'

const route = useRoute()
const activeIndex = computed(() => route.path)

const handleSelect = (key) => {
  console.log(key)
}
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
}

.logo-container {
  margin-right: auto;
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

/* 移除响应式折叠代码，确保导航始终横向显示 */
</style>