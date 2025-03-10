<template>
  <div class="cases-page">
    <!-- 页面标题 -->
    <div class="page-header">
      <div class="container">
        <h1 class="page-title">案例展示</h1>
        <p class="page-subtitle">呼和浩特本地商家抖音同城探店成功案例</p>
      </div>
    </div>
    
    <!-- 案例分类 -->
    <div class="section case-filter">
      <div class="container">
        <div class="filter-tabs">
          <el-radio-group v-model="activeCategory" size="large">
            <el-radio-button label="all">全部案例</el-radio-button>
            <el-radio-button label="kol">网红探店</el-radio-button>
            <el-radio-button label="brand">品牌推广</el-radio-button>
            <el-radio-button label="event">活动策划</el-radio-button>
            <el-radio-button label="content">内容创作</el-radio-button>
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
          <h3>项目背景</h3>
          <p>{{ selectedCase.background }}</p>
          
          <h3>项目目标</h3>
          <p>{{ selectedCase.goal }}</p>
          
          <h3>执行方案</h3>
          <p>{{ selectedCase.solution }}</p>
          
          <h3>项目成果</h3>
          <p>{{ selectedCase.result }}</p>
        </div>
      </div>
    </el-dialog>
    
    <!-- 合作流程 -->
    <div class="section cooperation-section">
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
    </div>
    
    <!-- 联系我们 -->
    <div class="section contact-section">
      <div class="container">
        <div class="contact-card">
          <h2>想要了解更多案例？</h2>
          <p>如果您对我们的案例有兴趣，或者想要了解更多合作细节，请随时联系我们。</p>
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
    title: '呼市知名火锅店抖音探店推广',
    category: 'kol',
    summary: '通过抖音同城探店内容，帮助呼和浩特知名火锅店提升品牌曝光和客流量，实现销售额显著增长。',
    date: '2023-05-15',
    background: '呼和浩特市知名火锅店希望通过抖音同城探店提升品牌知名度，吸引更多年轻消费群体。',
    goal: '通过与当地有影响力的美食博主合作，提高品牌在年轻消费群体中的认知度，增加门店客流量。',
    solution: '我们为商家匹配了3位在呼和浩特地区有较高影响力的美食博主，策划了一系列探店体验、美食评测和直播活动，通过真实体验分享增强用户信任。',
    result: '合作期间，商家抖音账号粉丝增长200%，门店日均客流量提升35%，周末需要提前两天预约，品牌在年轻人群中的知名度显著提高。'
  },
  {
    id: 2,
    title: '呼市商圈购物节抖音推广活动',
    category: 'event',
    summary: '为呼和浩特本地商圈策划并执行抖音同城购物节推广活动，带动整体客流量提升40%。',
    date: '2023-07-20',
    background: '呼和浩特市某大型商圈希望通过抖音同城活动提升整体客流量，带动商户销售增长。',
    goal: '通过创新的内容形式和多KOL联动，提升商圈知名度，吸引更多消费者到店消费。',
    solution: '我们组织了15位不同领域的呼市本地抖音达人，进行为期7天的商圈探店活动，创作了一系列短视频、图文和直播内容，全方位展示商圈魅力。',
    result: '活动内容总曝光量超过300万，带动商圈客流量提升40%，参与商户销售额平均增长25%，成功打造了商圈在抖音平台的品牌影响力。'
  },
  {
    id: 3,
    title: '呼市新开奶茶店抖音引流案例',
    category: 'brand',
    summary: '为呼和浩特新开奶茶店打造抖音同城引流方案，开业首月实现日均销售500杯。',
    date: '2023-09-10',
    background: '呼和浩特市新开奶茶品牌希望通过抖音同城营销快速打开市场，建立品牌知名度。',
    goal: '通过抖音同城探店内容，迅速提高品牌在目标消费群体中的认知度，带动开业期间的客流和销量。',
    solution: '我们为奶茶店定制了包括KOL探店、产品测评、开业活动策划和抖音话题挑战在内的整合营销方案。',
    result: '开业首月，品牌抖音账号粉丝突破5万，门店日均销售超过500杯，多款产品成为网红爆款，品牌迅速在呼市年轻人群中建立了知名度。'
  },
  {
    id: 4,
    title: '呼市健身房会员招募计划',
    category: 'content',
    summary: '通过抖音同城内容营销，帮助呼和浩特本地健身房在一个月内新增会员100+。',
    date: '2023-11-05',
    background: '呼和浩特市某连锁健身房希望通过抖音同城内容吸引更多潜在会员，提升会员转化率。',
    goal: '通过专业、有吸引力的健身内容，展示健身房的环境和服务，吸引目标用户到店体验并办理会员。',
    solution: '我们邀请了5位呼市本地健身领域KOL入驻健身房，创作一系列健身教学、器械使用和健身房环境展示的短视频内容，并策划了线上健身挑战活动。',
    result: '一个月内，健身房抖音账号涨粉2万+，到店体验人数增加200%，新增会员100+，会员转化率提升30%，成功建立了专业、年轻化的品牌形象。'
  },
  {
    id: 5,
    title: '呼市特色餐厅线上线下联动',
    category: 'kol',
    summary: '为呼和浩特特色蒙餐餐厅策划抖音同城探店活动，带动周末客流量翻倍增长。',
    date: '2024-01-15',
    background: '呼和浩特市一家特色蒙餐餐厅希望通过抖音同城探店提升品牌影响力，吸引更多外地游客和本地年轻人。',
    goal: '通过展示餐厅特色菜品和民族文化氛围，提升品牌在抖音平台的曝光度，增加客流量和销售额。',
    solution: '我们邀请了8位呼市本地美食、旅游和生活领域KOL进行探店体验，重点展示餐厅特色菜品和民族文化元素，并策划了线下互动活动。',
    result: '合作期间，餐厅相关抖音内容累计播放量超过200万，周末客流量翻倍增长，特色菜品销量提升60%，成功吸引了大量外地游客前来打卡。'
  },
  {
    id: 6,
    title: '呼市美容院会员回流计划',
    category: 'brand',
    summary: '通过抖音同城内容营销，帮助呼和浩特本地美容院激活沉睡会员，提升复购率40%。',
    date: '2024-02-20',
    background: '呼和浩特市某高端美容院面临会员活跃度下降的问题，希望通过抖音同城内容重新激活沉睡会员并吸引新客户。',
    goal: '通过专业、有吸引力的美容内容，重新唤起沉睡会员的兴趣，同时吸引新客户，提升整体营业额。',
    solution: '我们为美容院策划了一系列美容知识分享、护肤技巧和新项目展示的短视频内容，邀请3位呼市本地美妆KOL进行项目体验和真实评测。',
    result: '两个月内，沉睡会员激活率达到35%，会员复购率提升40%，新增会员60+，美容院月营业额提升25%，成功重塑了品牌形象。'
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
    'kol': '网红合作',
    'brand': '品牌推广',
    'event': '活动策划',
    'content': '内容创作'
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