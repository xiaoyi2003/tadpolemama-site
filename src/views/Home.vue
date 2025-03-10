<template>
  <div class="home">
    <!-- 轮播图部分 -->
    <div class="banner">
      <el-carousel height="500px">
        <el-carousel-item v-for="item in 3" :key="item">
          <div class="carousel-content" :class="`carousel-bg-${item}`">
            <div class="carousel-text">
              <h2>内蒙古默默文化传媒</h2>
              <p>呼和浩特抖音同城探店领先MCN机构，助力本地商家品牌增长</p>
              <el-button type="primary" size="large" @click="$router.push('/contact')">联系我们</el-button>
            </div>
          </div>
        </el-carousel-item>
      </el-carousel>
    </div>

    <!-- 关于我们简介 -->
    <div class="section about-section">
      <div class="container">
        <h2 class="section-title">关于我们</h2>
        <p class="section-subtitle">内蒙古默默文化传媒服务有限公司是呼和浩特地区领先的抖音同城探店MCN机构</p>
        
        <div class="about-content">
          <div class="about-text">
            <p>内蒙古默默文化传媒服务有限公司致力于为呼和浩特本地商家提供专业的抖音同城探店推广服务，拥有大量优质本地KOL资源和丰富的商家合作经验。我们通过精准的内容策划和高效的运营体系，帮助本地商家提升品牌曝光度和客流量，实现线上引流到线下消费的转化。</p>
            <el-button type="primary" plain @click="$router.push('/about')">了解更多</el-button>
          </div>
          <div class="about-image">
            <div class="image-placeholder">公司形象图</div>
          </div>
        </div>
      </div>
    </div>

    <!-- 服务内容 -->
    <div class="section service-section">
      <div class="container">
        <h2 class="section-title">我们的服务</h2>
        <p class="section-subtitle">为呼和浩特本地商家提供全方位的抖音营销服务</p>
        
        <div class="service-cards">
          <el-row :gutter="30">
            <el-col :xs="24" :sm="12" :md="8" v-for="(service, index) in services" :key="index">
              <div class="service-card">
                <div class="service-icon">
                  <i :class="service.icon"></i>
                </div>
                <h3>{{ service.title }}</h3>
                <p>{{ service.description }}</p>
              </div>
            </el-col>
          </el-row>
        </div>
        
        <div class="service-more">
          <el-button type="primary" plain @click="$router.push('/services')">查看全部服务</el-button>
        </div>
      </div>
    </div>

    <!-- 案例展示 -->
    <div class="section case-section">
      <div class="container">
        <h2 class="section-title">成功案例</h2>
        <p class="section-subtitle">我们的合作伙伴取得的成就</p>
        
        <div class="case-gallery">
          <el-row :gutter="20">
            <el-col :xs="24" :sm="12" :md="8" v-for="i in 6" :key="i">
              <div class="case-item">
                <div class="case-image">
                  <div class="image-placeholder">呼市商家案例 {{ i }}</div>
                </div>
                <div class="case-info">
                  <h3>呼市{{ ['餐饮', '美妆', '服饰', '娱乐', '健身', '教育'][i-1] }}商家推广案例</h3>
                  <p>通过抖音同城探店内容，帮助商家提升品牌曝光和客流量，实现业绩显著增长。</p>
                </div>
              </div>
            </el-col>
          </el-row>
        </div>
        
        <div class="case-more">
          <el-button type="primary" plain @click="$router.push('/cases')">查看更多案例</el-button>
        </div>
      </div>
    </div>

    <!-- 数据统计 -->
    <div class="section stats-section">
      <div class="container">
        <div class="stats-container">
          <div class="stat-item" v-for="(stat, index) in stats" :key="index">
            <div class="stat-number">{{ stat.number }}</div>
            <div class="stat-title">{{ stat.title }}</div>
          </div>
        </div>
      </div>
    </div>

    <!-- 联系我们 -->
    <div class="section contact-section">
      <div class="container">
        <h2 class="section-title">联系我们</h2>
        <p class="section-subtitle">随时为您提供专业的咨询和服务</p>
        
        <div class="contact-content">
          <div class="contact-info">
            <div class="contact-item">
              <i class="fas fa-map-marker-alt"></i>
              <span>内蒙古自治区呼和浩特市</span>
            </div>
            <div class="contact-item">
              <i class="fas fa-phone"></i>
              <span>400-123-4567</span>
            </div>
            <div class="contact-item">
              <i class="fas fa-envelope"></i>
              <span>contact@nmgmcn.com</span>
            </div>
          </div>
          
          <div class="contact-form">
            <el-form>
              <el-form-item>
                <el-input placeholder="您的姓名"></el-input>
              </el-form-item>
              <el-form-item>
                <el-input placeholder="您的电话"></el-input>
              </el-form-item>
              <el-form-item>
                <el-input placeholder="您的邮箱"></el-input>
              </el-form-item>
              <el-form-item>
                <el-input type="textarea" placeholder="您的留言" :rows="4"></el-input>
              </el-form-item>
              <el-form-item>
                <el-button type="primary">提交</el-button>
              </el-form-item>
            </el-form>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
import { ref } from 'vue'

const services = ref([
  {
    title: '网红孵化',
    icon: 'fas fa-user-friends',
    description: '发掘和培养呼和浩特本地有潜力的抖音达人，打造专业同城探店KOL团队。'
  },
  {
    title: '内容策划',
    icon: 'fas fa-lightbulb',
    description: '为呼市商家量身定制抖音同城探店内容，打造爆款视频，提升品牌曝光度。'
  },
  {
    title: '商业变现',
    icon: 'fas fa-hand-holding-usd',
    description: '连接呼市商家与本地KOL资源，实现线上引流到线下消费的高效转化。'
  },
  {
    title: '平台运营',
    icon: 'fas fa-chart-line',
    description: '专业的抖音账号运营和数据分析，提升呼市商家在同城页面的曝光和影响力。'
  },
  {
    title: '品牌推广',
    icon: 'fas fa-bullhorn',
    description: '为呼和浩特本地商家提供全方位抖音品牌营销方案，精准触达目标消费者。'
  },
  {
    title: '活动策划',
    icon: 'fas fa-calendar-alt',
    description: '策划和执行呼市商家线上线下联动活动，增强用户互动和品牌曝光。'
  }
])

const stats = ref([
  { number: '100+', title: '签约艺人' },
  { number: '500+', title: '合作商家' },
  { number: '1000万+', title: '粉丝覆盖' },
  { number: '5年+', title: '行业经验' }
])
</script>

<style scoped>
.home {
  overflow-x: hidden;
}

/* 轮播图样式 */
.banner {
  margin-bottom: 60px;
}

.carousel-content {
  height: 100%;
  display: flex;
  align-items: center;
  justify-content: center;
  color: white;
  background-size: cover;
  background-position: center;
}

.carousel-bg-1 {
  background-color: #409EFF;
}

.carousel-bg-2 {
  background-color: #67C23A;
}

.carousel-bg-3 {
  background-color: #E6A23C;
}

.carousel-text {
  text-align: center;
  max-width: 800px;
  padding: 0 20px;
}

.carousel-text h2 {
  font-size: 48px;
  margin-bottom: 20px;
}

.carousel-text p {
  font-size: 24px;
  margin-bottom: 30px;
}

/* 关于我们部分 */
.about-section {
  background-color: #f9f9f9;
}

.about-content {
  display: flex;
  align-items: center;
  gap: 40px;
}

.about-text {
  flex: 1;
}

.about-text p {
  margin-bottom: 20px;
  font-size: 16px;
  line-height: 1.8;
}

.about-image {
  flex: 1;
}

.image-placeholder {
  background-color: #e0e0e0;
  height: 300px;
  display: flex;
  align-items: center;
  justify-content: center;
  color: #666;
  font-size: 18px;
  border-radius: 8px;
}

/* 服务内容部分 */
.service-section {
  background-color: white;
}

.service-cards {
  margin-bottom: 40px;
}

.service-card {
  background-color: #fff;
  border-radius: 8px;
  padding: 30px;
  box-shadow: 0 4px 12px rgba(0, 0, 0, 0.05);
  text-align: center;
  height: 100%;
  transition: transform 0.3s, box-shadow 0.3s;
}

.service-card:hover {
  transform: translateY(-5px);
  box-shadow: 0 8px 24px rgba(0, 0, 0, 0.1);
}

.service-icon {
  font-size: 40px;
  color: #409EFF;
  margin-bottom: 20px;
}

.service-card h3 {
  font-size: 20px;
  margin-bottom: 15px;
  color: #333;
}

.service-card p {
  color: #666;
  line-height: 1.6;
}

.service-more {
  text-align: center;
  margin-top: 20px;
}

/* 案例展示部分 */
.case-section {
  background-color: #f9f9f9;
}

.case-gallery {
  margin-bottom: 40px;
}

.case-item {
  margin-bottom: 30px;
  background-color: #fff;
  border-radius: 8px;
  overflow: hidden;
  box-shadow: 0 4px 12px rgba(0, 0, 0, 0.05);
  transition: transform 0.3s, box-shadow 0.3s;
}

.case-item:hover {
  transform: translateY(-5px);
  box-shadow: 0 8px 24px rgba(0, 0, 0, 0.1);
}

.case-image {
  height: 200px;
}

.case-info {
  padding: 20px;
}

.case-info h3 {
  font-size: 18px;
  margin-bottom: 10px;
  color: #333;
}

.case-info p {
  color: #666;
  font-size: 14px;
  line-height: 1.6;
}

.case-more {
  text-align: center;
}

/* 数据统计部分 */
.stats-section {
  background-color: #409EFF;
  color: white;
  padding: 80px 0;
}

.stats-container {
  display: flex;
  justify-content: space-around;
  flex-wrap: wrap;
  text-align: center;
}

.stat-item {
  padding: 0 20px;
  margin-bottom: 20px;
}

.stat-number {
  font-size: 48px;
  font-weight: bold;
  margin-bottom: 10px;
}

.stat-title {
  font-size: 18px;
}

/* 联系我们部分 */
.contact-section {
  background-color: white;
}

.contact-content {
  display: flex;
  gap: 40px;
}

.contact-info {
  flex: 1;
  padding: 30px;
  background-color: #f9f9f9;
  border-radius: 8px;
}

.contact-item {
  margin-bottom: 20px;
  display: flex;
  align-items: center;
}

.contact-item i {
  font-size: 24px;
  color: #409EFF;
  margin-right: 15px;
  width: 24px;
}

.contact-form {
  flex: 1;
}

/* 响应式调整 */
@media (max-width: 768px) {
  .carousel-text h2 {
    font-size: 32px;
  }
  
  .carousel-text p {
    font-size: 18px;
  }
  
  .about-content {
    flex-direction: column;
  }
  
  .contact-content {
    flex-direction: column;
  }
  
  .stats-container {
    flex-direction: column;
  }
  
  .stat-item {
    width: 100%;
  }
}
</style>