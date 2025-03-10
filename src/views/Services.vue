<template>
  <div class="services-page">
    <!-- 页面标题 -->
    <div class="page-header">
      <div class="container">
        <h1 class="page-title">服务内容</h1>
        <p class="page-subtitle">为内容创作者提供全方位的专业服务</p>
      </div>
    </div>
    
    <!-- 服务介绍 -->
    <div class="section service-intro">
      <div class="container">
        <div class="intro-content">
          <div class="intro-text">
            <h2 class="section-title">我们的服务</h2>
            <p>内蒙古默默文化传媒服务有限公司作为专业的MCN机构，为内容创作者提供全方位的服务支持，帮助创作者实现内容价值最大化。</p>
            <p>我们拥有丰富的行业资源和专业的运营团队，能够为不同类型、不同阶段的创作者提供个性化的解决方案，助力创作者在激烈的内容市场中脱颖而出。</p>
          </div>
          <div class="intro-image">
            <div class="image-placeholder">服务概览图</div>
          </div>
        </div>
      </div>
    </div>
    
    <!-- 服务详情 -->
    <div class="section service-details">
      <div class="container">
        <div class="service-list">
          <div class="service-item" v-for="(service, index) in services" :key="index">
            <div class="service-icon">
              <i :class="service.icon"></i>
            </div>
            <div class="service-content">
              <h3>{{ service.title }}</h3>
              <p class="service-desc">{{ service.description }}</p>
              <div class="service-features">
                <ul>
                  <li v-for="(feature, i) in service.features" :key="i">
                    <i class="fas fa-check"></i> {{ feature }}
                  </li>
                </ul>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
    
    <!-- 服务流程 -->
    <div class="section process-section">
      <div class="container">
        <h2 class="section-title">服务流程</h2>
        <p class="section-subtitle">专业、高效的服务流程，确保创作者获得最佳体验</p>
        
        <div class="process-steps">
          <div class="process-step" v-for="(step, index) in processSteps" :key="index">
            <div class="step-number">{{ index + 1 }}</div>
            <div class="step-content">
              <h3>{{ step.title }}</h3>
              <p>{{ step.description }}</p>
            </div>
          </div>
        </div>
      </div>
    </div>
    
    <!-- 合作品牌 -->
    <div class="section brands-section">
      <div class="container">
        <h2 class="section-title">合作品牌</h2>
        <p class="section-subtitle">我们与众多知名品牌建立了长期稳定的合作关系</p>
        
        <div class="brand-logos">
          <el-row :gutter="30">
            <el-col :xs="12" :sm="8" :md="4" v-for="i in 12" :key="i">
              <div class="brand-logo">
                <div class="image-placeholder">品牌 {{ i }}</div>
              </div>
            </el-col>
          </el-row>
        </div>
      </div>
    </div>
    
    <!-- 联系我们 -->
    <div class="section contact-section">
      <div class="container">
        <div class="contact-card">
          <h2>需要更多服务信息？</h2>
          <p>如果您对我们的服务有任何疑问，或者想了解更多详情，请随时联系我们。</p>
          <el-button type="primary" size="large" @click="$router.push('/contact')">联系我们</el-button>
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
    description: '发掘和培养有潜力的内容创作者，提供专业培训和成长指导。',
    features: [
      '潜力创作者发掘与签约',
      '内容创作能力培训',
      '个人形象包装与定位',
      '粉丝运营与互动指导',
      '平台账号优化与成长'
    ]
  },
  {
    title: '内容策划',
    icon: 'fas fa-lightbulb',
    description: '为创作者提供内容创意和策划，打造爆款内容和个人IP。',
    features: [
      '内容方向规划与定位',
      '创意内容策划与制作',
      '热点话题捕捉与应用',
      '内容质量把控与优化',
      '个人IP打造与维护'
    ]
  },
  {
    title: '商业变现',
    icon: 'fas fa-hand-holding-usd',
    description: '对接品牌资源，开展商业合作，实现创作者价值最大化。',
    features: [
      '商业合作机会对接',
      '品牌推广内容策划',
      '商务谈判与合同管理',
      '直播带货策划与执行',
      '收益分析与优化'
    ]
  },
  {
    title: '平台运营',
    icon: 'fas fa-chart-line',
    description: '专业的账号运营和数据分析，提升粉丝互动和平台影响力。',
    features: [
      '多平台账号运营',
      '内容发布计划制定',
      '粉丝互动与维护',
      '数据分析与优化',
      '平台算法研究与应用'
    ]
  },
  {
    title: '品牌推广',
    icon: 'fas fa-bullhorn',
    description: '为品牌提供KOL营销解决方案，精准触达目标受众。',
    features: [
      'KOL资源匹配与推荐',
      '品牌营销策略制定',
      '内容营销方案设计',
      '营销效果监测与分析',
      '品牌声量提升方案'
    ]
  },
  {
    title: '活动策划',
    icon: 'fas fa-calendar-alt',
    description: '策划和执行线上线下活动，增强粉丝黏性和品牌曝光。',
    features: [
      '线上互动活动策划',
      '线下粉丝见面会组织',
      '品牌发布会策划执行',
      '跨平台联动活动',
      '活动效果评估与总结'
    ]
  }
])

const processSteps = ref([
  {
    title: '需求沟通',
    description: '深入了解创作者或品牌的需求和目标，进行初步沟通和评估。'
  },
  {
    title: '方案制定',
    description: '根据需求分析，制定个性化的服务方案，包括目标、策略和执行计划。'
  },
  {
    title: '签约合作',
    description: '确认服务内容和合作细节，签订合作协议，明确双方权责。'
  },
  {
    title: '执行实施',
    description: '专业团队按计划执行各项工作，定期沟通进度和调整优化方向。'
  },
  {
    title: '效果评估',
    description: '对服务效果进行全面评估和数据分析，提供详细的效果报告。'
  },
  {
    title: '持续优化',
    description: '根据评估结果，不断优化服务内容和策略，实现长期稳定合作。'
  }
])
</script>

<style scoped>
.services-page {
  overflow-x: hidden;
}

/* 页面标题样式 */
.page-header {
  background-color: #409EFF;
  color: white;
  padding: 80px 0;
  text-align: center;
  margin-bottom: 60px;
}

.page-title {
  font-size: 48px;
  margin-bottom: 20px;
}

.page-subtitle {
  font-size: 24px;
  opacity: 0.8;
}

/* 服务介绍部分 */
.intro-content {
  display: flex;
  gap: 40px;
  align-items: center;
  margin-bottom: 40px;
}

.intro-text {
  flex: 1;
}

.intro-text p {
  margin-bottom: 20px;
  line-height: 1.8;
  font-size: 16px;
}

.intro-image {
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
/* 服务详情部分 */
.service-details {
  background-color: #f9f9f9;
  padding: 80px 0;
}

.service-list {
  display: flex;
  flex-direction: column;
  gap: 30px;
}

.service-item {
  display: flex;
  background-color: white;
  border-radius: 8px;
  overflow: hidden;
  box-shadow: 0 4px 12px rgba(0, 0, 0, 0.05);
  transition: transform 0.3s, box-shadow 0.3s;
}

.service-item:hover {
  transform: translateY(-5px);
  box-shadow: 0 8px 24px rgba(0, 0, 0, 0.1);
}

.service-icon {
  display: flex;
  align-items: center;
  justify-content: center;
  width: 150px;
  background-color: #409EFF;
  color: white;
  font-size: 48px;
}

.service-content {
  flex: 1;
  padding: 30px;
}

.service-content h3 {
  font-size: 24px;
  margin-bottom: 15px;
  color: #333;
}

.service-desc {
  margin-bottom: 20px;
  color: #666;
  line-height: 1.6;
}

.service-features ul {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(250px, 1fr));
  gap: 10px;
  list-style: none;
  padding: 0;
}

.service-features li {
  display: flex;
  align-items: center;
  color: #666;
}

.service-features li i {
  color: #67C23A;
  margin-right: 10px;
}

/* 服务流程部分 */
.process-section {
  padding: 80px 0;
}

.process-steps {
  max-width: 800px;
  margin: 40px auto 0;
  position: relative;
}

.process-steps::before {
  content: '';
  position: absolute;
  top: 0;
  bottom: 0;
  left: 35px;
  width: 4px;
  background-color: #409EFF;
}

.process-step {
  position: relative;
  padding-left: 80px;
  margin-bottom: 40px;
}

.step-number {
  position: absolute;
  left: 0;
  top: 0;
  width: 70px;
  height: 70px;
  background-color: #409EFF;
  color: white;
  border-radius: 50%;
  display: flex;
  align-items: center;
  justify-content: center;
  font-size: 24px;
  font-weight: bold;
  z-index: 1;
}

.step-content {
  background-color: white;
  padding: 25px;
  border-radius: 8px;
  box-shadow: 0 4px 12px rgba(0, 0, 0, 0.05);
}

.step-content h3 {
  margin-bottom: 10px;
  color: #333;
}

.step-content p {
  color: #666;
  line-height: 1.6;
}

/* 合作品牌部分 */
.brands-section {
  background-color: #f9f9f9;
  padding: 80px 0;
}

.brand-logos {
  margin-top: 40px;
}

.brand-logo {
  height: 100px;
  margin-bottom: 30px;
  display: flex;
  align-items: center;
  justify-content: center;
}

.brand-logo .image-placeholder {
  width: 100%;
  height: 100%;
  background-color: #e0e0e0;
  display: flex;
  align-items: center;
  justify-content: center;
  border-radius: 8px;
}
</style>