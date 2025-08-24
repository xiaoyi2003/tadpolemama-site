<template>
  <div class="cases-page">
    <!-- 页面标题 -->
    <div class="page-header">
      <div class="container">
        <h1 class="page-title">案例展示</h1>
        <p class="page-subtitle">一些真实的服务案例</p>
      </div>
    </div>
    
    <!-- 案例分类 -->
    <div class="section case-filter">
      <div class="container">
        <div class="filter-tabs">
          <el-radio-group v-model="activeCategory" size="large">
            <el-radio-button label="all">全部案例</el-radio-button>
            <el-radio-button label="kol">月子中心</el-radio-button>
            <el-radio-button label="brand">月嫂平台</el-radio-button>
            <!-- <el-radio-button label="event"></el-radio-button>
            <el-radio-button label="content"></el-radio-button> -->
          </el-radio-group>
        </div>
      </div>
    </div>
    
    <!-- 案例展示 -->
    <div class="section case-gallery">
      <div class="container">
        <div class="cases-grid">
          <el-row :gutter="30">
            <el-col :xs="24" :sm="12" :md="8" v-for="(caseItem, index) in filteredCases" :key="index">
              <div class="case-card" @click="showCaseDetail(caseItem)">
                <div class="case-image">
                  <div class="image-placeholder">{{ caseItem.title }} 图片</div>
                  <div class="case-category">{{ getCategoryName(caseItem.category) }}</div>
                </div>
                <div class="case-info">
                  <h3>{{ caseItem.title }}</h3>
                  <p>{{ caseItem.summary }}</p>
                  <div class="case-meta">
                    <span><i class="fas fa-calendar"></i> {{ caseItem.date }}</span>
                    <span class="view-more">查看详情 <i class="fas fa-arrow-right"></i></span>
                  </div>
                </div>
              </div>
            </el-col>
          </el-row>
        </div>
      </div>
    </div>
    
    <!-- 案例详情弹窗 -->
    <el-dialog
      v-model="dialogVisible"
      title="案例详情"
      width="70%"
      :before-close="handleClose"
    >
      <div v-if="selectedCase" class="case-detail">
        <div class="case-detail-header">
          <h2>{{ selectedCase.title }}</h2>
          <div class="case-detail-meta">
            <span><i class="fas fa-calendar"></i> {{ selectedCase.date }}</span>
            <span><i class="fas fa-tag"></i> {{ getCategoryName(selectedCase.category) }}</span>
          </div>
        </div>
        
        <div class="case-detail-image">
          <div class="image-placeholder">{{ selectedCase.title }} 详情图片</div>
        </div>
        
        <div class="case-detail-content">
          <h3>客户背景</h3>
          <p>{{ selectedCase.background }}</p>
          
          <h3>项遇到的问题</h3>
          <p>{{ selectedCase.goal }}</p>
          
          <h3>服务方案</h3>
          <p>{{ selectedCase.solution }}</p>
          
          <h3>结果与反馈</h3>
          <p>{{ selectedCase.result }}</p>
        </div>
      </div>
    </el-dialog>
    
    <!-- 合作流程 -->
    <!-- <div class="section cooperation-section">
      <div class="container">
        <h2 class="section-title">合作流程</h2>
        <p class="section-subtitle">专业高效的项目执行流程，确保合作成功</p>
        
        <div class="cooperation-steps">
          <el-row :gutter="20">
            <el-col :xs="24" :sm="12" :md="6" v-for="(step, index) in cooperationSteps" :key="index">
              <div class="cooperation-step">
                <div class="step-icon">
                  <i :class="step.icon"></i>
                </div>
                <h3>{{ step.title }}</h3>
                <p>{{ step.description }}</p>
              </div>
            </el-col>
          </el-row>
        </div>
      </div>
    </div> -->
    
    <!-- 联系我们 -->
    <div class="section contact-section">
      <div class="container">
        <div class="contact-card">
          <h2>想要了解更多案例？</h2>
          <p></p>
          <el-button type="primary" size="large" @click="$router.push('/contact')">联系我们</el-button>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
import { ref, computed } from 'vue'

const activeCategory = ref('all')
const dialogVisible = ref(false)
const selectedCase = ref(null)

const cases = ref([
  {
    id: 1,
    title: '初为人母的温馨守护',
    category: 'kol',
    summary: '张女士是一位第一次当妈妈的年轻客户，在生产后出现了情绪波动和哺乳困难。入住我们月子中心后，护理团队为她制定了专属的产后恢复方案。',
    date: '2025-05-15',
    background: '',
    goal: '',
    solution: '',
    result: ''
  },
  {
    id: 2,
    title: '二胎妈妈的科学照护',
    category: 'brand',
    summary: '',
    date: '2025-07-20',
    background: '',
    goal: '',
    solution: '',
    result: ''
  },
  {
           id: 3,
    title: '',
    category: 'brand',
    summary: '',
    date: '',
    background: '',
    solution: '',
    result: ''
  },
  {
           id: 4,
    title: '',
    category: 'brand',
    summary: '',
    date: '',
    background: '',
    solution: '',
    result: ''
  },
  {
       id: 5,
    title: '',
    category: 'brand',
    summary: '',
    date: '',
    background: '',
    solution: '',
    result: ''
  },
  {
    id: 6,
    title: '',
    category: 'brand',
    summary: '',
    date: '',
    background: '',
    solution: '',
    result: ''
  }
])

const filteredCases = computed(() => {
  if (activeCategory.value === 'all') {
    return cases.value
  } else {
    return cases.value.filter(caseItem => caseItem.category === activeCategory.value)
  }
})

const cooperationSteps = ref([
  {
    icon: 'fas fa-comments',
    title: '需求沟通',
    description: '深入了解客户需求和目标'
  },
  {
    icon: 'fas fa-lightbulb',
    title: '方案制定',
    description: '制定个性化的执行方案'
  },
  {
    icon: 'fas fa-handshake',
    title: '签约合作',
    description: '确认合作细节，签订协议'
  },
  {
    icon: 'fas fa-tasks',
    title: '执行实施',
    description: '专业团队高效执行方案'
  }
])

const showCaseDetail = (caseItem) => {
  selectedCase.value = caseItem
  dialogVisible.value = true
}

const handleClose = () => {
  dialogVisible.value = false
}

const getCategoryName = (category) => {
  const categoryMap = {
    'kol': '月子中心',
    'brand': '月嫂平台',
    'event': '',
    'content': ''
  }
  return categoryMap[category] || '其他'
}
</script>

<style scoped>
.cases-page {
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
  font-weight: 300; /* 更轻盈的字重 */
  letter-spacing: 1px; /* 增加字母间距 */
}

.page-subtitle {
  font-size: 24px;
  opacity: 0.8;
  font-weight: 300; /* 更轻盈的字重 */
  letter-spacing: 0.5px; /* 增加字母间距 */
}

/* 案例分类部分 */
.case-filter {
  margin-bottom: 40px;
}

.filter-tabs {
  display: flex;
  justify-content: center;
}

/* 案例展示部分 */
.case-gallery {
  padding-top: 0;
}

.case-card {
  background-color: white;
  border-radius: 8px;
  overflow: hidden;
  box-shadow: 0 4px 12px rgba(0, 0, 0, 0.05);
  margin-bottom: 30px;
  cursor: pointer;
  transition: transform 0.3s, box-shadow 0.3s;
  height: 100%;
}

.case-card:hover {
  transform: translateY(-5px);
  box-shadow: 0 8px 24px rgba(0, 0, 0, 0.1);
}

.case-image {
  height: 200px;
  position: relative;
}

.case-category {
  position: absolute;
  top: 10px;
  right: 10px;
  background-color: rgba(64, 158, 255, 0.8);
  color: white;
  padding: 5px 10px;
  border-radius: 4px;
  font-size: 12px;
  font-weight: 500; /* 稍微加粗 */
  letter-spacing: 0.5px; /* 增加字母间距 */
  text-transform: uppercase; /* 转为大写，增加设计感 */
}

.case-info {
  padding: 20px;
}

.case-info h3 {
  font-size: 20px; /* 增大标题字号 */
  margin-bottom: 12px; /* 增加下边距 */
  color: #333;
  font-weight: 500; /* 适中的字重 */
  letter-spacing: 0.3px; /* 增加字母间距 */
  line-height: 1.4; /* 增加行高 */
}

.case-info p {
  color: #666;
  margin-bottom: 15px;
  line-height: 1.6; /* 增加行高，提高可读性 */
  font-size: 14px; /* 调整字体大小 */
  font-weight: 400; /* 正常字重 */
}

/* 案例元数据样式 */
.case-meta {
  display: flex;
  justify-content: space-between;
  align-items: center;
  font-size: 13px;
  color: #888;
}

.case-meta span {
  display: flex;
  align-items: center;
}

.case-meta i {
  margin-right: 5px;
}

.view-more {
  color: #409EFF;
  font-weight: 500;
  transition: color 0.3s;
}

.view-more:hover {
  color: #66b1ff;
}

/* 案例详情弹窗样式 */
.case-detail-header {
  margin-bottom: 30px;
}

.case-detail-header h2 {
  font-size: 28px;
  margin-bottom: 15px;
  color: #333;
  font-weight: 500;
  letter-spacing: 0.5px;
}

.case-detail-meta {
  display: flex;
  gap: 20px;
  color: #666;
  font-size: 14px;
}

.case-detail-meta span {
  display: flex;
  align-items: center;
}

.case-detail-meta i {
  margin-right: 8px;
}

.case-detail-image {
  margin-bottom: 30px;
}

.case-detail-content h3 {
  font-size: 22px;
  margin: 25px 0 15px;
  color: #333;
  font-weight: 500;
  letter-spacing: 0.3px;
}

.case-detail-content p {
  color: #666;
  line-height: 1.8;
  margin-bottom: 20px;
  font-size: 15px;
}

/* 合作流程部分 */
.cooperation-section {
  background-color: #f9f9f9;
  padding: 80px 0;
}

.cooperation-steps {
  margin-top: 40px;
}

.cooperation-step {
  text-align: center;
  padding: 30px 20px;
  background-color: white;
  border-radius: 8px;
  box-shadow: 0 4px 12px rgba(0, 0, 0, 0.05);
  height: 100%;
  transition: transform 0.3s, box-shadow 0.3s;
}

.cooperation-step:hover {
  transform: translateY(-5px);
  box-shadow: 0 8px 24px rgba(0, 0, 0, 0.1);
}

.step-icon {
  font-size: 36px;
  color: #409EFF;
  margin-bottom: 20px;
}

.cooperation-step h3 {
  font-size: 20px;
  margin-bottom: 15px;
  color: #333;
  font-weight: 500;
  letter-spacing: 0.3px;
}

.cooperation-step p {
  color: #666;
  line-height: 1.6;
  font-size: 14px;
}

/* 联系我们部分 */
.contact-section {
  padding: 60px 0;
}

.contact-card {
  background-color: #409EFF;
  color: white;
  padding: 40px;
  border-radius: 8px;
  text-align: center;
  box-shadow: 0 4px 20px rgba(64, 158, 255, 0.2);
}

.contact-card h2 {
  font-size: 28px;
  margin-bottom: 15px;
  font-weight: 500;
  letter-spacing: 0.5px;
}

.contact-card p {
  margin-bottom: 25px;
  font-size: 16px;
  opacity: 0.9;
  max-width: 600px;
  margin-left: auto;
  margin-right: auto;
  line-height: 1.6;
  font-weight: 300;
}

/* 响应式调整 */
@media (max-width: 768px) {
  .page-title {
    font-size: 36px;
  }
  
  .page-subtitle {
    font-size: 18px;
  }
  
  .case-info h3 {
    font-size: 18px;
  }
  
  .case-detail-header h2 {
    font-size: 24px;
  }
  
  .case-detail-content h3 {
    font-size: 20px;
  }
  
  .contact-card h2 {
    font-size: 24px;
  }
}
</style>