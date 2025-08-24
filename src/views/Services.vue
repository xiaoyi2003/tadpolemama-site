<template>
  <div class="services-page">
    <!-- 页面标题 -->
    <div class="page-header">
      <div class="container">
        <h1 class="page-title">Tadpolemama月子中心</h1>
        <p class="page-subtitle">我们用专业与关爱，陪伴每一位新手妈妈与宝宝，度过温馨而安心的月子时光。</p>
      </div>
    </div>
    
    <!-- 服务介绍 -->
    <div class="section service-intro">
      <div class="container">
        <div class="intro-content">
          <div class="intro-text">
            <h2 class="section-title">环境介绍</h2>
            <p>Tadpolemama 月子中心 坐落于城市优质生活区，环境清幽、交通便利。这里不仅为产后妈妈和新生儿提供舒适的居住环境，更拥有完善的周边配套，方便家人探访与日常生活。</p>
            <p>交通便利：紧邻地铁与公交站点，家人探访方便快捷，减少舟车劳顿。
              医疗资源丰富：周边有三甲医院及专业儿科医疗机构，确保妈妈和宝宝在特殊情况下能够第一时间得到医疗支持。
              活设施齐全：附近商场、超市、药房一应俱全，家属生活无忧。
              自然环境优越：月子中心周围绿化率高，毗邻城市公园和湖景区域，空气清新，有利于妈妈身心放松与产后恢复。</p>
          </div>
          <div class="intro-image">
            <div class="image-placeholder">环境照片</div>
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
    
    <!--  -->
    <!-- <div class="section process-section">
      <div class="container">
        <h2 class="section-title">服务流程</h2>
        <p class="section-subtitle">专业、高效的服务流程，确保商家获得最佳营销效果</p>
        
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
    </div> -->
    
    <!-- 合作品牌 -->
    <div class="section brands-section">
      <div class="container">
        <h2 class="section-title">合作商家</h2>
        <p class="section-subtitle">我们已与众多知名本地商家建立了长期稳定的合作关系</p>
        
        <div class="brand-logos">
          <el-row :gutter="30">
            <el-col :xs="12" :sm="8" :md="4" v-for="i in 12" :key="i">
              <div class="brand-logo">
                <div class="image-placeholder"> {{ i }}</div>
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
          <h2></h2>
          <p></p>
          <el-button type="primary" size="large" @click="$router.push('/contact')">联系我们</el-button>
        </div>
      </div>
    </div>
  </div>
</template>


<!-- 套餐介绍 -->
 <!-- <script setup>
import { ref } from 'vue'  

const services = ref([
  {
    title: '产妇护理服务',
    // icon: 'fas fa-user-friends',
    description: '',
    features: [
      '产后恢复指导（盆底修复、形体恢复、伤口护理）',
      '产后饮食营养配餐（科学月子餐）',
      '情绪关怀与心理疏导（产后抑郁预防）',
      '乳房护理与母乳喂养指导',
  
    ]
  },
  {
    title: '新生儿护理服务',
    // icon: 'fas fa-lightbulb',
    description: '',
    features: [
      '新生儿日常照护（洗澡、抚触、喂养、排泄）',
      '黄疸观察与护理',
      '新生儿睡眠训练与安全指导',
      '新生儿常见疾病的早期识别',
      
    ]
  },
  {
    title: '健康监测服务',
    // icon: 'fas fa-hand-holding-usd',
    description: '',
    features: [
      '产妇定期体检（体温、血压、恢复情况）',
      '新生儿健康监测（体重、黄疸、发育情况）',
      '提供专业医生巡诊或合作医院转诊',
     
    ]
  },
  {
    title: '营养与饮食服务',
    // icon: 'fas fa-chart-line',
    description: '',
    features: [
      '定制化月子餐（分阶段科学搭配）',
      '针对不同体质的食疗调理',
      '健康饮品与中医养生汤品',
   
    ]
  },
  {
    title: '休养与环境服务',
    // icon: 'fas fa-bullhorn',
    description: '',
    features: [
      '高品质住宿环境（单间/套房，安全舒适）',
      '母婴同室或婴儿单独托管选择',
      '专属安静空间与安全消毒系统',
 
    ]
  },
  {
    title: '特色增值服务',
    // icon: 'fas fa-calendar-alt',
    description: '',
    features: [
      '宝宝摄影与成长记录',
      '家庭育儿课程（父母课堂）',
      '上门月嫂或延伸服务（出月子后继续护理）',
      '产后康复项目（瑜伽、轻运动、保健）',
    ]
  }
])

const processSteps = ref([
  {
    title: '需求沟通',
    description: '深入了解呼市商家的需求和目标，进行初步沟通和评估。'
  },
  {
    title: '方案制定',
    description: '根据商家特点和目标受众，制定个性化的抖音同城探店推广方案。'
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
    description: '根据效果评估结果，持续优化推广策略，确保长期稳定的营销效果。'
  }
])
</script> -->
<!-- 服务介绍 -->
<script setup>
import { ref } from 'vue'  

const services = ref([
  {
    title: '产妇护理服务',
    // icon: 'fas fa-user-friends',
    description: '',
    features: [
      '产后恢复指导（盆底修复、形体恢复、伤口护理）',
      '产后饮食营养配餐（科学月子餐）',
      '情绪关怀与心理疏导（产后抑郁预防）',
      '乳房护理与母乳喂养指导',
  
    ]
  },
  {
    title: '新生儿护理服务',
    // icon: 'fas fa-lightbulb',
    description: '',
    features: [
      '新生儿日常照护（洗澡、抚触、喂养、排泄）',
      '黄疸观察与护理',
      '新生儿睡眠训练与安全指导',
      '新生儿常见疾病的早期识别',
      
    ]
  },
  {
    title: '健康监测服务',
    // icon: 'fas fa-hand-holding-usd',
    description: '',
    features: [
      '产妇定期体检（体温、血压、恢复情况）',
      '新生儿健康监测（体重、黄疸、发育情况）',
      '提供专业医生巡诊或合作医院转诊',
     
    ]
  },
  {
    title: '营养与饮食服务',
    // icon: 'fas fa-chart-line',
    description: '',
    features: [
      '定制化月子餐（分阶段科学搭配）',
      '针对不同体质的食疗调理',
      '健康饮品与中医养生汤品',
   
    ]
  },
  {
    title: '休养与环境服务',
    // icon: 'fas fa-bullhorn',
    description: '',
    features: [
      '高品质住宿环境（单间/套房，安全舒适）',
      '母婴同室或婴儿单独托管选择',
      '专属安静空间与安全消毒系统',
 
    ]
  },
  {
    title: '特色增值服务',
    // icon: 'fas fa-calendar-alt',
    description: '',
    features: [
      '宝宝摄影与成长记录',
      '家庭育儿课程（父母课堂）',
      '上门月嫂或延伸服务（出月子后继续护理）',
      '产后康复项目（瑜伽、轻运动、保健）',
    ]
  }
])

const processSteps = ref([
  {
    title: '需求沟通',
    description: '深入了解呼市商家的需求和目标，进行初步沟通和评估。'
  },
  {
    title: '方案制定',
    description: '根据商家特点和目标受众，制定个性化的抖音同城探店推广方案。'
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
    description: '根据效果评估结果，持续优化推广策略，确保长期稳定的营销效果。'
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

/* 响应式调整 */
@media (max-width: 768px) {
  .page-title {
    font-size: 36px;
  }
  
  .page-subtitle {
    font-size: 18px;
  }
  
  .intro-content {
    flex-direction: column;
  }
  
  .service-item {
    flex-direction: column;
  }
  
  .service-icon {
    width: 100%;
    height: 100px;
  }
  
  .service-features ul {
    grid-template-columns: 1fr;
  }
  
  .process-steps::before {
    left: 25px;
  }
  
  .process-step {
    padding-left: 60px;
  }
  
  .step-number {
    width: 50px;
    height: 50px;
    font-size: 18px;
  }
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