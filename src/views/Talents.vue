<template>
  <div class="talents-page">
    <!-- 页面标题 -->
    <div class="page-header">
      <div class="container">
        <h1 class="page-title">艺人资源</h1>
        <p class="page-subtitle">呼和浩特本地抖音同城探店KOL资源</p>
      </div>
    </div>
    
    <!-- 艺人分类 -->
    <div class="section talent-filter">
      <div class="container">
        <div class="filter-tabs">
          <el-radio-group v-model="activeCategory" size="large">
            <el-radio-button label="all">全部艺人</el-radio-button>
            <el-radio-button label="kol">抖音达人</el-radio-button>
            <el-radio-button label="singer">歌手音乐人</el-radio-button>
            <el-radio-button label="actor">演员主持</el-radio-button>
            <el-radio-button label="dancer">舞者模特</el-radio-button>
          </el-radio-group>
        </div>
      </div>
    </div>
    
    <!-- 艺人展示 -->
    <div class="section talent-gallery">
      <div class="container">
        <div class="talents-grid">
          <el-row :gutter="30">
            <el-col :xs="24" :sm="12" :md="8" :lg="6" v-for="(talent, index) in filteredTalents" :key="index">
              <div class="talent-card" @click="showTalentDetail(talent)">
                <div class="talent-image">
                  <div class="image-placeholder">{{ talent.name }} 照片</div>
                  <div class="talent-category">{{ getCategoryName(talent.category) }}</div>
                </div>
                <div class="talent-info">
                  <h3>{{ talent.name }}</h3>
                  <p class="talent-tags">
                    <el-tag v-for="(tag, i) in talent.tags" :key="i" size="small" effect="plain" class="tag-item">
                      {{ tag }}
                    </el-tag>
                  </p>
                  <div class="talent-stats">
                    <div class="stat-item">
                      <i class="fas fa-heart"></i>
                      <span>{{ talent.fans }}</span>
                    </div>
                    <div class="stat-item">
                      <i class="fas fa-play-circle"></i>
                      <span>{{ talent.views }}</span>
                    </div>
                  </div>
                </div>
              </div>
            </el-col>
          </el-row>
        </div>
      </div>
    </div>
    
    <!-- 艺人详情弹窗 -->
    <el-dialog
      v-model="dialogVisible"
      title="艺人详情"
      width="70%"
      :before-close="handleClose"
    >
      <div v-if="selectedTalent" class="talent-detail">
        <div class="talent-detail-header">
          <div class="talent-detail-image">
            <div class="image-placeholder">{{ selectedTalent.name }} 照片</div>
          </div>
          <div class="talent-detail-info">
            <h2>{{ selectedTalent.name }}</h2>
            <p class="talent-detail-category">{{ getCategoryName(selectedTalent.category) }}</p>
            <p class="talent-detail-tags">
              <el-tag v-for="(tag, i) in selectedTalent.tags" :key="i" size="small" effect="plain" class="tag-item">
                {{ tag }}
              </el-tag>
            </p>
            <div class="talent-detail-stats">
              <div class="stat-item">
                <i class="fas fa-heart"></i>
                <span>粉丝数：{{ selectedTalent.fans }}</span>
              </div>
              <div class="stat-item">
                <i class="fas fa-play-circle"></i>
                <span>播放量：{{ selectedTalent.views }}</span>
              </div>
              <div class="stat-item">
                <i class="fas fa-thumbs-up"></i>
                <span>互动率：{{ selectedTalent.engagement }}</span>
              </div>
            </div>
          </div>
        </div>
        
        <div class="talent-detail-content">
          <h3>个人简介</h3>
          <p>{{ selectedTalent.bio }}</p>
          
          <h3>内容特色</h3>
          <p>{{ selectedTalent.content }}</p>
          
          <h3>合作案例</h3>
          <p>{{ selectedTalent.cases }}</p>
          
          <h3>合作咨询</h3>
          <p>如果您对与{{ selectedTalent.name }}的合作感兴趣，请联系我们的商务团队进行详细咨询。</p>
          <el-button type="primary" @click="$router.push('/contact')">联系我们</el-button>
        </div>
      </div>
    </el-dialog>
    
    <!-- 合作优势 -->
    <div class="section advantage-section">
      <div class="container">
        <h2 class="section-title">合作优势</h2>
        <p class="section-subtitle">选择与我们合作的理由</p>
        
        <div class="advantages">
          <el-row :gutter="30">
            <el-col :xs="24" :sm="12" :md="8" v-for="(advantage, index) in advantages" :key="index">
              <div class="advantage-card">
                <div class="advantage-icon">
                  <i :class="advantage.icon"></i>
                </div>
                <h3>{{ advantage.title }}</h3>
                <p>{{ advantage.description }}</p>
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
          <h2>寻找合适的艺人资源？</h2>
          <p>如果您正在寻找合适的艺人进行合作，我们可以根据您的需求提供最佳匹配方案。</p>
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
const selectedTalent = ref(null)

const talents = ref([
  {
    id: 1,
    name: '李明',
    category: 'kol',
    tags: ['美食', '同城探店', '生活方式'],
    fans: '120万+',
    views: '5000万+',
    engagement: '5.8%',
    bio: '呼和浩特知名美食博主，擅长发掘和推广呼市特色美食，以幽默风趣的视频风格获得大量粉丝喜爱。',
    content: '以呼市本地餐厅探店、美食测评和特色小吃推荐为主，视频风格轻松有趣，画面精美，深受年轻用户喜爱。',
    cases: '已为呼和浩特50+家餐饮商家提供抖音同城探店服务，平均为商家带来客流量提升30%，多家合作商家成为网红打卡地。'
  },
  {
    id: 2,
    name: '草原风',
    category: 'singer',
    tags: ['民族音乐', '文化推广', '蒙古族'],
    fans: '85万+',
    views: '3200万+',
    engagement: '6.2%',
    bio: '呼和浩特著名音乐人，擅长将传统蒙古族音乐元素与现代音乐风格相结合，为多家呼市商家创作品牌主题曲。',
    content: '以原创歌曲和呼市文化场所探访为主，音乐风格独特，充满民族特色，为呼市多家文化场馆带来大量客流。',
    cases: '为呼和浩特多家文化场馆、特色餐厅和旅游景点创作主题音乐并进行抖音推广，帮助合作商家提升品牌形象和客流量。'
  },
  {
    id: 3,
    name: '小雪',
    category: 'kol',
    tags: ['美妆', '时尚', '同城探店'],
    fans: '95万+',
    views: '4500万+',
    engagement: '5.5%',
    bio: '呼和浩特人气美妆博主，擅长化妆技巧分享和产品测评，经常探访呼市美妆店铺和美容机构。',
    content: '以美妆教程、呼市美容院和美妆店探店为主，内容专业且实用，深受呼和浩特年轻女性用户喜爱。',
    cases: '与呼和浩特30+家美妆店铺和美容机构合作，进行抖音同城探店推广，平均为商家带来销售额提升25%。'
  },
  {
    id: 4,
    name: '阿拉腾',
    category: 'dancer',
    tags: ['蒙古族舞蹈', '文化推广', '场地探访'],
    fans: '75万+',
    views: '2800万+',
    engagement: '6.8%',
    bio: '呼和浩特著名舞者，擅长蒙古族传统舞蹈和现代舞蹈，经常在呼市各文化场所和商业空间表演。',
    content: '以舞蹈表演、呼市文化场所探访为主，作品充满民族特色和艺术感染力，为呼市多家场馆带来大量客流。',
    cases: '为呼和浩特多家商场、文化中心和旅游景点策划舞蹈表演并进行抖音推广，提升场所人气和品牌形象。'
  },
  {
    id: 5,
    name: '张伟',
    category: 'actor',
    tags: ['主持人', '活动探访', '商家推广'],
    fans: '65万+',
    views: '2500万+',
    engagement: '5.2%',
    bio: '呼和浩特知名主持人，擅长活动主持和商家探访，语言风趣幽默，经常为呼市商家活动进行抖音直播。',
    content: '以呼市商家活动报道、新店开业探访为主，内容轻松有趣，互动性强，深受呼和浩特各年龄段观众喜爱。',
    cases: '主持过呼和浩特50+场商业活动并进行抖音同城直播，平均为活动带来线上观看量10万+，有效提升商家品牌曝光。'
  },
  {
    id: 6,
    name: '青青',
    category: 'kol',
    tags: ['亲子', '教育机构探访', '家庭生活'],
    fans: '110万+',
    views: '4800万+',
    engagement: '7.2%',
    bio: '呼和浩特知名亲子博主，分享育儿经验和家庭生活，经常探访呼市各大亲子场所和教育机构。',
    content: '以呼市亲子场所探店、教育机构评测为主，内容温馨有爱，实用性强，深受呼和浩特年轻父母喜爱。',
    cases: '与呼和浩特40+家亲子场所、教育机构合作，进行抖音同城探店推广，平均为合作机构带来咨询量提升45%。'
  },
  {
    id: 7,
    name: '草原鹰',
    category: 'kol',
    tags: ['户外', '景点探访', '旅游推广'],
    fans: '80万+',
    views: '3500万+',
    engagement: '6.5%',
    bio: '呼和浩特知名户外博主，专注于呼市及周边自然风光和人文景观的探索与记录，以震撼的视觉作品著称。',
    content: '以呼和浩特周边景点探访、特色民宿推荐为主，内容震撼壮美，展现呼市独特的自然风光和人文魅力。',
    cases: '与呼和浩特及周边30+家景区、民宿合作，进行抖音同城探店推广，平均为景区带来游客量提升35%。'
  },
  {
    id: 8,
    name: '乌日娜',
    category: 'singer',
    tags: ['民族歌手', '文化场所探访', '传统音乐'],
    fans: '70万+',
    views: '2600万+',
    engagement: '6.0%',
    bio: '呼和浩特蒙古族歌手，擅长传统蒙古族音乐演唱，经常在呼市各文化场所和特色餐厅表演。',
    content: '以传统歌曲演唱、呼市文化场所和特色餐厅探访为主，展现呼和浩特独特的民族文化魅力。',
    cases: '为呼和浩特20+家蒙餐厅和文化场所进行抖音同城探店推广，帮助合作商家打造民族特色品牌形象。'
  }
])

const filteredTalents = computed(() => {
  if (activeCategory.value === 'all') {
    return talents.value
  } else {
    return talents.value.filter(talent => talent.category === activeCategory.value)
  }
})

const advantages = ref([
  {
    icon: 'fas fa-users',
    title: '本地KOL资源',
    description: '拥有呼和浩特地区最丰富的抖音同城KOL资源库，覆盖各行业领域，能为商家提供精准匹配的达人资源。'
  },
  {
    icon: 'fas fa-map-marker-alt',
    title: '本地市场洞察',
    description: '深耕呼和浩特本地市场多年，了解本地消费者习惯和偏好，能为商家提供更有针对性的营销策略。'
  },
  {
    icon: 'fas fa-chart-line',
    title: '数据驱动决策',
    description: '通过专业的数据分析系统，实时监测呼市同城探店内容效果，持续优化营销策略，提升投资回报率。'
  },
  {
    icon: 'fas fa-handshake',
    title: '一站式服务',
    description: '为呼和浩特本地商家提供从内容策划、KOL匹配到效果评估的全流程服务，省心省力高效率。'
  },
  {
    icon: 'fas fa-award',
    title: '成功案例保障',
    description: '已成功服务呼市500+家本地商家，拥有丰富的同城探店推广经验和成功案例，确保合作效果。'
  },
  {
    icon: 'fas fa-sync-alt',
    title: '持续创新',
    description: '紧跟抖音同城算法和市场趋势变化，不断创新内容形式和营销方式，帮助呼市商家保持竞争优势。'
  }
])

const cooperationSteps = ref([
  {
    icon: 'fas fa-comments',
    title: '需求沟通',
    description: '了解您的品牌需求和合作目标'
  },
  {
    icon: 'fas fa-user-check',
    title: '艺人匹配',
    description: '推荐最适合的艺人资源'
  },
  {
    icon: 'fas fa-file-contract',
    title: '方案确认',
    description: '确定合作内容和执行计划'
  },
  {
    icon: 'fas fa-tasks',
    title: '执行落地',
    description: '专业团队全程跟进合作执行'
  }
])

const showTalentDetail = (talent) => {
  selectedTalent.value = talent
  dialogVisible.value = true
}

const handleClose = () => {
  dialogVisible.value = false
}

const getCategoryName = (category) => {
  const categoryMap = {
    'kol': '网红博主',
    'singer': '歌手音乐人',
    'actor': '演员主持',
    'dancer': '舞者模特'
  }
  return categoryMap[category] || '其他'
}
</script>

<style scoped>
.talents-page {
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

/* 艺人分类部分 */
.talent-filter {
  margin-bottom: 40px;
}

.filter-tabs {
  display: flex;
  justify-content: center;
}

/* 艺人展示部分 */
.talent-gallery {
  padding-top: 0;
}

.talent-card {
  background-color: white;
  border-radius: 8px;
  overflow: hidden;
  box-shadow: 0 4px 12px rgba(0, 0, 0, 0.05);
  margin-bottom: 30px;
  cursor: pointer;
  transition: transform 0.3s, box-shadow 0.3s;
}

.talent-card:hover {
  transform: translateY(-5px);
  box-shadow: 0 8px 24px rgba(0, 0, 0, 0.1);
}

.talent-image {
  height: 250px;
  position: relative;
}

.talent-category {
  position: absolute;
  top: 10px;
  right: 10px;
  background-color: rgba(64, 158, 255, 0.8);
  color: white;
  padding: 5px 10px;
  border-radius: 4px;
  font-size: 12px;
}

.talent-info {
  padding: 20px;
}

.talent-info h3 {
  font-size: 18px;
  margin-bottom: 10px;
  color: #333;
}

.talent-tags {
  margin-bottom: 15px;
}

.tag-item {
  margin-right: 5px;
  margin-bottom: 5px;
}

.talent-stats {
  display: flex;
  justify-content: space-between;
  color: #666;
  font-size: 14px;
}

.stat-item {
  display: flex;
  align-items: center;
}

.stat-item i {
  color: #409EFF;
  margin-right: 5px;
}

/* 艺人详情弹窗 */
.talent-detail-header {
  display: flex;
  gap: 30px;
  margin-bottom: 30px;
}

.talent-detail-image {
  width: 300px;
  height: 300px;
}

.talent-detail-info {
  flex: 1;
}

.talent-detail-info h2 {
  font-size: 24px;
  margin-bottom: 10px;
  color: #333;
}

.talent-detail-category {
  color: #409EFF;
  font-weight: bold;
  margin-bottom: 15px;
}

.talent-detail-tags {
  margin-bottom: 20px;
}

.talent-detail-stats {
  display: flex;
  flex-direction: column;
  gap: 10px;
  color: #666;
}

.talent-detail-content {
  border-top: 1px solid #eee;
  padding-top: 30px;
}

.talent-detail-content h3 {
  font-size: 18px;
  margin: 20px 0 10px;
  color: #333;
}

.talent-detail-content p {
  color: #666;
  line-height: 1.8;
  margin-bottom: 20px;
}

/* 合作优势部分 */
.advantage-section {
  background-color: #f9f9f9;
  padding: 80px 0;
}

.advantages {
  margin-top: 40px;
}

.advantage-card {
  background-color: white;
  border-radius: 8px;
  padding: 30px;
  text-align: center;
  box-shadow: 0 4px 12px rgba(0, 0, 0, 0.05);
  height: 100%;
  transition: transform 0.3s, box-shadow 0.3s;
}

.advantage-card:hover {
  transform: translateY(-5px);
  box-shadow: 0 8px 24px rgba(0, 0, 0, 0.1);
}

.advantage-icon {
  font-size: 48px;
  color: #409EFF;
  margin-bottom: 20px;
}

.advantage-card h3 {
  font-size: 20px;
  margin-bottom: 15px;
  color: #333;
}

.advantage-card p {
  color: #666;
  line-height: 1.6;
}

/* 联系我们部分 */
.contact-section {
  padding: 60px 0;
}

.contact-card {
  background-color: #f5f7fa;
  border-radius: 8px;
  padding: 40px;
  text-align: center;
}

.contact-card h2 {
  font-size: 28px;
  color: #333;
  margin-bottom: 15px;
}

.contact-card p {
  color: #666;
  margin-bottom: 30px;
  font-size: 16px;
  line-height: 1.6;
}

/* 响应式调整 */
@media (max-width: 768px) {
  .page-header {
    padding: 60px 0;
  }

  .page-title {
    font-size: 36px;
  }

  .page-subtitle {
    font-size: 18px;
  }

  .talent-detail-header {
    flex-direction: column;
  }

  .talent-detail-image {
    width: 100%;
    height: 200px;
    margin-bottom: 20px;
  }

  .contact-card {
    padding: 30px 20px;
  }
}
</style>