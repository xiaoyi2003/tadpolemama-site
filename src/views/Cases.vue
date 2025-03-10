<template>
  <div class="cases-page">
    <!-- 页面标题 -->
    <div class="page-header">
      <div class="container">
        <h1 class="page-title">案例展示</h1>
        <p class="page-subtitle">我们的成功案例和合作伙伴</p>
      </div>
    </div>
    
    <!-- 案例分类 -->
    <div class="section case-filter">
      <div class="container">
        <div class="filter-tabs">
          <el-radio-group v-model="activeCategory" size="large">
            <el-radio-button label="all">全部案例</el-radio-button>
            <el-radio-button label="kol">网红合作</el-radio-button>
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
    title: '知名美妆博主合作推广',
    category: 'kol',
    summary: '与知名美妆博主合作，为国际化妆品品牌进行产品推广，实现销售额显著增长。',
    date: '2023-05-15',
    background: '国际知名化妆品品牌希望在内蒙古地区扩大市场份额，提高品牌知名度和产品销量。',
    goal: '通过与当地有影响力的美妆博主合作，提高品牌在年轻消费群体中的认知度，促进产品销售。',
    solution: '我们为品牌匹配了5位在内蒙古地区有较高影响力的美妆博主，策划了一系列产品体验、评测和直播活动，通过真实体验分享增强用户信任。',
    result: '合作期间，品牌在内蒙古地区的销售额同比增长35%，品牌搜索量提升40%，成功建立了品牌在当地的影响力。'
  },
  {
    id: 2,
    title: '内蒙古特色文化推广活动',
    category: 'event',
    summary: '策划并执行内蒙古特色文化推广系列活动，提升地区文化影响力和旅游吸引力。',
    date: '2023-07-20',
    background: '内蒙古旅游局希望通过新媒体渠道推广当地特色文化和旅游资源，吸引更多游客。',
    goal: '通过创新的内容形式和多平台传播，展示内蒙古的自然风光、民族文化和特色美食，提升旅游吸引力。',
    solution: '我们组织了10位不同领域的内容创作者，进行为期15天的内蒙古文化探索之旅，创作了一系列短视频、图文和直播内容，全方位展示内蒙古魅力。',
    result: '活动内容总曝光量超过5000万，互动量超过300万，相关话题登上多个平台热搜榜，活动期间当地旅游咨询量增长50%。'
  },
  {
    id: 3,
    title: '本地餐饮品牌线上推广',
    category: 'brand',
    summary: '为本地连锁餐饮品牌打造全方位线上推广方案，提升品牌知名度和门店客流量。',
    date: '2023-09-10',
    background: '本地知名连锁餐饮品牌希望通过新媒体营销提升品牌形象，吸引年轻消费群体。',
    goal: '提高品牌在年轻人群中的认知度和好感度，增加门店客流量和销售额。',
    solution: '我们为品牌定制了包括短视频内容创作、KOL合作、社交媒体运营和线下线上联动活动在内的整合营销方案。',
    result: '三个月内，品牌社交媒体粉丝增长200%，门店客流量提升25%，品牌知名度显著提高，成功吸引了更多年轻消费者。'
  },
  {
    id: 4,
    title: '音乐人才培养计划',
    category: 'content',
    summary: '发掘和培养本地音乐创作人才，打造原创音乐IP，实现内容价值最大化。',
    date: '2023-11-05',
    background: '内蒙古地区拥有丰富的音乐文化资源，但缺乏系统的新生代音乐人才培养和推广渠道。',
    goal: '发掘和培养具有潜力的本地音乐创作者，帮助他们提升创作水平和影响力，打造原创音乐IP。',
    solution: '我们启动了"草原新声"音乐人才培养计划，为15位有潜力的音乐创作者提供专业培训、创作指导和推广资源，帮助他们创作和发行原创音乐作品。',
    result: '项目孵化的15首原创歌曲获得超过500万次播放，3位音乐人成功签约音乐厂牌，项目获得多家媒体报道，为内蒙古音乐文化发展注入新活力。'
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
}

.page-subtitle {
  font-size: 24px;
  opacity: 0.8;
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
  margin-bottom: 15px;
  line-height: 1;
}
</style>