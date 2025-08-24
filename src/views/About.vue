<template>
  <div class="about-page">
    <!-- 页面标题 -->
    <div class="page-header">
      <div class="container">
        <h1 class="page-title">关于我们</h1>
        <p class="page-subtitle">Tadpolemama 母婴</p>
      </div>
    </div>
    
    <!-- 公司简介 -->

    
        <div class="section company-intro">
      <div class="container">
        <div class="intro-content">
          <div class="intro-text">
            <h2 class="section-title">品牌故事</h2>
            <p>Tadpolemama 的创始人李女士曾在自己产后护理过程中，发现市面上缺乏真正专业又贴心的母婴护理服务。</p>
            <p>她希望每位妈妈都能得到全面的关爱，每个宝宝都能健康成长。于是，她组建了 Tadpolemama 团队，从选拔培训月嫂、设计个性化护理方案到提供科学饮食与生活指导，力求为母婴家庭打造最安心、温暖的护理体验。</p>
            <p>Tadpolemama 的每一位成员都秉承“专业、温暖、守护”的理念，把每一个家庭当作自己的家，用心服务每一位妈妈和宝宝。</p>
          </div>
          <div class="intro-image">
            <div class="image-placeholder">品牌logo</div>
          </div>
        </div>
      </div>
    </div>
    <!-- 创始人介绍 -->
        <div class="section company-intro">
      <div class="container">
        <div class="intro-content">
          <div class="intro-text">
            <h2 class="section-title">创始人介绍</h2>
            <p>于女士</p>
            <p>于女士拥有多年母婴护理和产后康复经验，是 Tadpolemama 的创始人兼负责人。她曾在自己的产后护理过程中，深刻体会到专业、贴心护理的重要性。为了让每位妈妈和宝宝都能获得科学、全面的照护，她创立了 Tadpolemama，组建了一支经验丰富、专业可靠的月嫂团队。</p>
            <p>于女士注重团队培训和服务质量，倡导“专业、温暖、守护”的理念，致力于为母婴家庭打造温馨、安全、科学的护理体验。</p>
          </div>
          <div class="intro-image">
            <div class="image-placeholder">照片</div>
          </div>
        </div>
      </div>
    </div>
    <!-- 企业文化 -->
    <!-- <div class="section company-culture">
      <div class="container">
        <h2 class="section-title">企业文化</h2>
        <div class="culture-content">
          <div class="culture-item">
            <div class="culture-icon">
              <i class="fas fa-eye"></i>
            </div>
            <h3>愿景</h3>
            <p>成为内蒙古地区最具影响力的内容创作平台，推动本土文化创意产业发展。</p>
          </div>
          <div class="culture-item">
            <div class="culture-icon">
              <i class="fas fa-bullseye"></i>
            </div>
            <h3>使命</h3>
            <p>发掘优秀创作者，赋能内容创作，连接品牌与用户，创造多元价值。</p>
          </div>
          <div class="culture-item">
            <div class="culture-icon">
              <i class="fas fa-heart"></i>
            </div>
            <h3>价值观</h3>
            <p>创新、专业、诚信、共赢、责任。</p>
          </div>
        </div>
      </div>
    </div> -->
    
    <!-- 发展历程 -->
    <!-- <div class="section company-history">
      <div class="container">
        <h2 class="section-title">发展历程</h2>
        <div class="timeline">
          <div class="timeline-item">
            <div class="timeline-year">2018</div>
            <div class="timeline-content">
              <h3>公司成立</h3>
              <p>内蒙古默默文化传媒服务有限公司在呼和浩特市成立。</p>
            </div>
          </div>
          <div class="timeline-item">
            <div class="timeline-year">2019</div>
            <div class="timeline-content">
              <h3>业务拓展</h3>
              <p>签约首批20名内容创作者，开始提供专业MCN服务。</p>
            </div>
          </div>
          <div class="timeline-item">
            <div class="timeline-year">2020</div>
            <div class="timeline-content">
              <h3>规模扩大</h3>
              <p>签约艺人突破50人，与多家知名品牌建立合作关系。</p>
            </div>
          </div>
          <div class="timeline-item">
            <div class="timeline-year">2021</div>
            <div class="timeline-content">
              <h3>业务多元化</h3>
              <p>拓展直播电商业务，成功举办多场线下活动。</p>
            </div>
          </div>
          <div class="timeline-item">
            <div class="timeline-year">2022</div>
            <div class="timeline-content">
              <h3>战略升级</h3>
              <p>签约艺人突破100人，粉丝总量超过1000万。</p>
            </div>
          </div>
          <div class="timeline-item">
            <div class="timeline-year">2023</div>
            <div class="timeline-content">
              <h3>持续创新</h3>
              <p>推出创作者成长计划，加强本土文化内容创作。</p>
            </div>
          </div>
        </div>
      </div>
    </div> -->
    
    <!-- 团队介绍 -->
    <!-- <div class="section team-section">
      <div class="container">
        <h2 class="section-title">核心团队</h2>
        <p class="section-subtitle">专业的团队是我们最大的财富</p>
        
        <div class="team-members">
          <el-row :gutter="30">
            <el-col :xs="24" :sm="12" :md="8" v-for="i in 6" :key="i">
              <div class="team-member">
                <div class="member-avatar">
                  <div class="image-placeholder">头像</div>
                </div>
                <div class="member-info">
                  <h3>团队成员 {{ i }}</h3>
                  <p class="member-position">职位名称</p>
                  <p class="member-desc">简短的个人介绍和专业背景描述。</p>
                </div>
              </div>
            </el-col>
          </el-row>
        </div>
      </div>
    </div> -->
  </div>
</template>

<script setup>
// 无需额外的脚本逻辑
</script>

<style scoped>

.about-page {
  overflow-x: hidden;
  background-color: #ffffff; /* 设置整体页面背景为白色 */
  color: #333; /* 文字颜色避免太淡 */
}

.image-placeholder {
  background-color: #f0f0f0; /* 占位图区域改成浅灰，不会黑色 */
  color: #666;
  display: flex;
  align-items: center;
  justify-content: center;
  height: 200px;
  border-radius: 8px;
}

.about-page {
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

/* 公司简介部分 */
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
  color: hsl(0, 59%, 46%); 
}

.intro-image {
  flex: 1;
}

/* 企业文化部分 */
.company-culture {
  background-color: #f9f9f9;
  padding: 80px 0;
}

.culture-content {
  display: flex;
  justify-content: space-between;
  flex-wrap: wrap;
  gap: 30px;
  margin-top: 40px;
}

.culture-item {
  flex: 1;
  min-width: 300px;
  text-align: center;
  padding: 30px;
  background-color: white;
  border-radius: 8px;
  box-shadow: 0 4px 12px rgba(0, 0, 0, 0.05);
}

.culture-icon {
  font-size: 48px;
  color: #409EFF;
  margin-bottom: 20px;
}

.culture-item h3 {
  font-size: 24px;
  margin-bottom: 15px;
  color: #333;
}

.culture-item p {
  color: #666;
  line-height: 1.6;
}

/* 发展历程部分 */
.company-history {
  padding: 80px 0;
}

.timeline {
  position: relative;
  max-width: 800px;
  margin: 40px auto 0;
  padding: 20px 0;
}

.timeline::before {
  content: '';
  position: absolute;
  top: 0;
  bottom: 0;
  left: 120px;
  width: 4px;
  background-color: #409EFF;
}

.timeline-item {
  position: relative;
  margin-bottom: 40px;
  padding-left: 160px;
}

.timeline-year {
  position: absolute;
  left: 0;
  width: 100px;
  text-align: right;
  font-size: 24px;
  font-weight: bold;
  color: #409EFF;
}

.timeline-content {
  background-color: white;
  padding: 20px;
  border-radius: 8px;
  box-shadow: 0 4px 12px rgba(0, 0, 0, 0.05);
}

.timeline-content h3 {
  margin-bottom: 10px;
  color: #333;
}

.timeline-content p {
  color: #666;
  line-height: 1.6;
}

/* 团队介绍部分 */
.team-section {
  background-color: #f9f9f9;
  padding: 80px 0;
}

.team-members {
  margin-top: 40px;
}

.team-member {
  background-color: white;
  border-radius: 8px;
  overflow: hidden;
  box-shadow: 0 4px 12px rgba(0, 0, 0, 0.05);
  margin-bottom: 30px;
  transition: transform 0.3s, box-shadow 0.3s;
}

.team-member:hover {
  transform: translateY(-5px);
  box-shadow: 0 8px 24px rgba(0, 0, 0, 0.1);
}

.member-avatar {
  height: 250px;
  overflow: hidden;
}

.member-info {
  padding: 20px;
}

.member-info h3 {
  font-size: 20px;
  margin-bottom: 5px;
  color: #333;
}

.member-position {
  color: #409EFF;
  font-weight: bold;
  margin-bottom: 10px;
}

.member-desc {
  color: #666;
  font-size: 14px;
  line-height: 1.6;
}

/* 响应式调整 */
@media (max-width: 768px) {
  .intro-content {
    flex-direction: column;
  }
  
  .culture-content {
    flex-direction: column;
  }
  
  .timeline::before {
    left: 30px;
  }
  
  .timeline-item {
    padding-left: 70px;
  }
  
  .timeline-year {
    width: auto;
    text-align: left;
    left: 40px;
    top: 0;
  }
  
  .timeline-content {
    margin-top: 30px;
  }
}
</style>