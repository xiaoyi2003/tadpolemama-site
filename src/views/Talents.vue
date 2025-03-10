<template>
  <div class="talents-page">
    <!-- 页面标题 -->
    <div class="page-header">
      <div class="container">
        <h1 class="page-title">艺人资源</h1>
        <p class="page-subtitle">我们的签约艺人和合作资源</p>
      </div>
    </div>
    
    <!-- 艺人分类 -->
    <div class="section talent-filter">
      <div class="container">
        <div class="filter-tabs">
          <el-radio-group v-model="activeCategory" size="large">
            <el-radio-button label="all">全部艺人</el-radio-button>
            <el-radio-button label="kol">网红博主</el-radio-button>
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
    tags: ['美食', '生活方式', '旅行'],
    fans: '120万+',
    views: '5000万+',
    engagement: '5.8%',
    bio: '内蒙古知名美食博主，擅长发掘和推广内蒙古特色美食，以幽默风趣的视频风格获得大量粉丝喜爱。',
    content: '以探店、美食制作教程和美食文化介绍为主，视频风格轻松有趣，画面精美，深受年轻用户喜爱。',
    cases: '曾与多家知名餐饮品牌、食品品牌合作，策划的美食节目在短视频平台获得超过1亿次播放。'
  },
  {
    id: 2,
    name: '草原风',
    category: 'singer',
    tags: ['民族音乐', '原创歌手', '蒙古族'],
    fans: '85万+',
    views: '3200万+',
    engagement: '6.2%',
    bio: '内蒙古著名音乐人，擅长将传统蒙古族音乐元素与现代音乐风格相结合，创作出独具特色的音乐作品。',
    content: '以原创歌曲和翻唱作品为主，音乐风格独特，充满民族特色，同时兼具现代感和国际化视野。',
    cases: '发行多张个人专辑，举办多场线下演唱会，参与多个音乐节演出，作品《草原的呼唤》获得年度最佳民族音乐奖。'
  },
  {
    id: 3,
    name: '小雪',
    category: 'kol',
    tags: ['美妆', '时尚', '穿搭'],
    fans: '95万+',
    views: '4500万+',
    engagement: '5.5%',
    bio: '内蒙古人气美妆博主，擅长化妆技巧分享和产品测评，以专业、真实的内容获得用户信任。',
    content: '以美妆教程、产品测评和日常穿搭为主，内容专业且实用，深受年轻女性用户喜爱。',
    cases: '与多家国内外知名美妆品牌合作，参与多个美妆活动和新品发布会，推荐的产品多次售罄。'
  },
  {
    id: 4,
    name: '阿拉腾',
    category: 'dancer',
    tags: ['蒙古族舞蹈', '编舞', '舞蹈教学'],
    fans: '75万+',
    views: '2800万+',
    engagement: '6.8%',
    bio: '内蒙古著名舞者，擅长蒙古族传统舞蹈和现代舞蹈，曾获得多项舞蹈大赛奖项。',
    content: '以舞蹈表演、编舞和舞蹈教学为主，作品充满民族特色和艺术感染力，展现草原文化魅力。',
    cases: '参与多个大型文艺演出和晚会，为多个品牌活动编排舞蹈节目，开设线上舞蹈课程广受欢迎。'
  },
  {
    id: 5,
    name: '张伟',
    category: 'actor',
    tags: ['主持人', '脱口秀', '活动主持'],
    fans: '65万+',
    views: '2500万+',
    engagement: '5.2%',
    bio: '内蒙古知名主持人，擅长活动主持和脱口秀表演，语言风趣幽默，反应机智灵活。',
    content: '以活动主持、脱口秀和生活分享为主，内容轻松有趣，互动性强，深受各年龄段观众喜爱。',
    cases: '主持过多个大型活动和晚会，参与多个综艺节目录制，为多个品牌代言和推广。'
  },
  {
    id: 6,
    name: '青青',
    category: 'kol',
    tags: ['亲子', '育儿', '家庭生活'],
    fans: '110万+',
    views: '4800万+',
    engagement: '7.2%',
    bio: '内蒙古知名亲子博主，分享育儿经验和家庭生活，以温暖真实的内容风格获得大量家庭用户的喜爱。',
    content: '以育儿知识分享、亲子活动和家庭日常为主，内容温馨有爱，实用性强，深受年轻父母喜爱。',
    cases: '与多家母婴品牌、教育机构合作，参与多个亲子活动和公益项目，推出的亲子课程广受欢迎。'
  },
  {
    id: 7,
    name: '草原鹰',
    category: 'kol',
    tags: ['户外', '摄影', '探险'],
    fans: '80万+',
    views: '3500万+',
    engagement: '6.5%',
    bio: '内蒙古知名户外博主，专注于内蒙古自然风光和人文景观的探索与记录，以震撼的视觉作品著称。',
    content: '以户外探险、风光摄影和文化探访为主，内容震撼壮美，展现内蒙古独特的自然风光和人文魅力。',
    cases: '与多家旅游机构、户外装备品牌合作，参与多个地区旅游推广项目，出版的摄影集广受好评。'
  },
  {
    id: 8,
    name: '乌日娜',
    category: 'singer',
    tags: ['民族歌手', '马头琴', '传统音乐'],
    fans: '70万+',
    views: '2600万+',
    engagement: '6.0%',
    bio: '内蒙古著名民族歌手，擅长传统蒙古族歌曲演唱和马头琴演奏，致力于传统音乐的传承与创新。',
    content: '以传统歌曲演唱、马头琴演奏和音乐教学为主，内容具有浓厚的民族特色和文化底蕴。',
    cases: '举办多场个人音乐会，参与多个文化交流活动，录制的传统音乐专辑在国内外广受好评。'
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
    title: '丰富的艺人资源',
    description: '拥有100+签约艺人，覆盖各类内容领域，满足不同品牌和活动的需求。'
  },
  {
    icon: 'fas fa-bullseye',
    title: '精准的匹配服务',
    description: '根据品牌调性和目标受众，提供最适合的艺人资源，实现营销效果最大化。'
  },
  {
    icon: 'fas fa-handshake',
    title: '专业的合作管理',
    description: '全程跟进合作过程，确保沟通顺畅、执行高效、成果优质。'
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