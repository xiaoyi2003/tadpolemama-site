<template>
  <div class="contact-page">
    <!-- 页面标题 -->
    <div class="page-header">
      <div class="container">
        <h1 class="page-title">联系我们</h1>
        <p class="page-subtitle">随时为您提供专业的咨询和服务</p>
      </div>
    </div>
    
    <!-- 联系信息 -->
    <div class="section contact-info-section">
      <div class="container">
        <div class="contact-content">
          <div class="contact-details">
            <h2 class="section-title">联系方式</h2>
            <p class="contact-desc">如果您是呼和浩特本地商家，希望通过抖音同城探店提升品牌曝光和客流量，欢迎随时联系我们，获取专业的营销解决方案。</p>
            
            <div class="info-items">
              <div class="info-item">
                <div class="info-icon">
                  <i class="fas fa-map-marker-alt"></i>
                </div>
                <div class="info-content">
                  <h3>公司地址</h3>
                  <p>内蒙古自治区呼和浩特市赛罕区</p>
                </div>
              </div>
              
              <div class="info-item">
                <div class="info-icon">
                  <i class="fas fa-phone"></i>
                </div>
                <div class="info-content">
                  <h3>联系电话</h3>
                  <p>400-123-4567</p>
                </div>
              </div>
              
              <div class="info-item">
                <div class="info-icon">
                  <i class="fas fa-envelope"></i>
                </div>
                <div class="info-content">
                  <h3>电子邮箱</h3>
                  <p>contact@nmgmcn.com</p>
                </div>
              </div>
              
              <div class="info-item">
                <div class="info-icon">
                  <i class="fas fa-clock"></i>
                </div>
                <div class="info-content">
                  <h3>工作时间</h3>
                  <p>周一至周五 9:00-18:00</p>
                </div>
              </div>
            </div>
            
            <div class="social-media">
              <h3>关注我们</h3>
              <div class="social-icons">
                <a href="#" class="social-icon"><i class="fab fa-weixin"></i></a>
                <a href="#" class="social-icon"><i class="fab fa-weibo"></i></a>
                <a href="#" class="social-icon"><i class="fab fa-tiktok"></i></a>
                <a href="#" class="social-icon"><i class="fab fa-bilibili"></i></a>
              </div>
            </div>
          </div>
          
          <div class="contact-form-container">
            <h2 class="section-title">商家合作咨询</h2>
            <p class="form-desc">请填写以下表单，我们的抖音同城探店推广专家将尽快与您联系。</p>
            
            <el-form :model="form" :rules="rules" ref="contactForm" label-position="top">
              <el-form-item label="商家名称" prop="name">
                <el-input v-model="form.name" placeholder="请输入您的商家名称"></el-input>
              </el-form-item>
              
              <el-form-item label="联系电话" prop="phone">
                <el-input v-model="form.phone" placeholder="请输入您的联系电话"></el-input>
              </el-form-item>
              
              <el-form-item label="电子邮箱" prop="email">
                <el-input v-model="form.email" placeholder="请输入您的电子邮箱"></el-input>
              </el-form-item>
              
              <el-form-item label="合作意向" prop="interest">
                <el-select v-model="form.interest" placeholder="请选择合作意向" style="width: 100%">
                  <el-option label="抖音同城探店" value="抖音同城探店"></el-option>
                  <el-option label="KOL营销合作" value="KOL营销合作"></el-option>
                  <el-option label="品牌推广活动" value="品牌推广活动"></el-option>
                  <el-option label="短视频内容制作" value="短视频内容制作"></el-option>
                  <el-option label="线上线下活动策划" value="线上线下活动策划"></el-option>
                  <el-option label="其他合作" value="其他合作"></el-option>
                </el-select>
              </el-form-item>
              
              <el-form-item label="留言内容" prop="message">
                <el-input type="textarea" v-model="form.message" rows="5" placeholder="请简要描述您的需求和期望"></el-input>
              </el-form-item>
              
              <el-form-item>
                <el-button type="primary" size="large">提交咨询</el-button>
              </el-form-item>
            </el-form>
          </div>
        </div>
      </div>
    </div>
    
    <!-- 常见问题 -->
    <div class="section faq-section">
      <div class="container">
        <h2 class="section-title">常见问题</h2>
        <div class="faq-content">
          <el-collapse>
            <el-collapse-item title="抖音同城探店能给商家带来哪些好处？" name="1">
              <div>抖音同城探店可以帮助呼和浩特本地商家提升品牌曝光度，增加店铺客流量，提高销售转化率。通过专业KOL真实体验和推荐，能够建立消费者信任，吸引更多潜在客户。</div>
            </el-collapse-item>
            <el-collapse-item title="贵公司提供哪些服务？" name="2">
              <div>我们提供抖音同城探店、KOL营销、内容策划、商业变现、平台运营、品牌推广和活动策划等全方位MCN服务，可以根据呼和浩特本地商家需求提供定制化解决方案。</div>
            </el-collapse-item>
            <el-collapse-item title="如何选择适合的艺人进行合作？" name="3">
              <div>我们会根据您的商家类型、目标受众和营销目标，为您推荐最适合的呼和浩特本地KOL资源，并提供专业的匹配建议，确保合作效果最大化。</div>
            </el-collapse-item>
            <el-collapse-item title="合作流程是怎样的？" name="4">
              <div>一般包括需求沟通、方案制定、签约合作、执行实施、效果评估和持续优化六个步骤，我们会全程跟进，确保合作顺利进行。</div>
            </el-collapse-item>
            <el-collapse-item title="如何评估合作效果？" name="5">
              <div>我们会根据事先约定的KPI指标，如曝光量、互动量、转化率等，提供详细的数据报告和效果分析，帮助您评估合作成果。</div>
            </el-collapse-item>
          </el-collapse>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
import { ref, reactive } from 'vue'
import { ElMessage } from 'element-plus'

const contactForm = ref(null)

const form = reactive({
  name: '',
  phone: '',
  email: '',
  interest: '',
  message: ''
})

const rules = {
  name: [
    { required: true, message: '请输入您的姓名', trigger: 'blur' }
  ],
  phone: [
    { required: true, message: '请输入您的联系电话', trigger: 'blur' }
  ],
  email: [
    { required: true, message: '请输入您的电子邮箱', trigger: 'blur' },
    { type: 'email', message: '请输入正确的邮箱格式', trigger: 'blur' }
  ],
  interest: [
    { required: true, message: '请选择合作意向', trigger: 'change' }
  ],
  message: [
    { required: true, message: '请输入留言内容', trigger: 'blur' }
  ]
}

const submitForm = () => {
  contactForm.value.validate((valid) => {
    if (valid) {
      // 这里可以添加表单提交逻辑
      ElMessage({
        message: '留言提交成功，我们将尽快与您联系！',
        type: 'success'
      })
      // 重置表单
      contactForm.value.resetFields()
    } else {
      ElMessage.error('请完善表单信息')
      return false
    }
  })
}
</script>

<style scoped>
.contact-page {
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

/* 联系信息部分 */
.contact-content {
  display: flex;
  gap: 40px;
  margin-bottom: 40px;
}

.contact-details {
  flex: 1;
  background-color: #f9f9f9;
  padding: 30px;
  border-radius: 8px;
}

.contact-desc {
  margin-bottom: 30px;
  color: #666;
  line-height: 1.6;
}

.info-items {
  display: flex;
  flex-direction: column;
  gap: 20px;
  margin-bottom: 30px;
}

.info-item {
  display: flex;
  align-items: flex-start;
}

.info-icon {
  width: 50px;
  height: 50px;
  background-color: #409EFF;
  color: white;
  border-radius: 50%;
  display: flex;
  align-items: center;
  justify-content: center;
  font-size: 20px;
  margin-right: 15px;
}

.info-content h3 {
  font-size: 18px;
  margin-bottom: 5px;
  color: #333;
}

.info-content p {
  color: #666;
}

.social-media h3 {
  font-size: 18px;
  margin-bottom: 15px;
  color: #333;
}

.social-icons {
  display: flex;
  gap: 15px;
}

.social-icon {
  width: 40px;
  height: 40px;
  background-color: #409EFF;
  color: white;
  border-radius: 50%;
  display: flex;
  align-items: center;
  justify-content: center;
  font-size: 20px;
  transition: background-color 0.3s;
}

.social-icon:hover {
  background-color: #66b1ff;
}

/* 联系表单部分 */
.contact-form-container {
  flex: 1;
  background-color: white;
  padding: 30px;
  border-radius: 8px;
  box-shadow: 0 4px 12px rgba(0, 0, 0, 0.05);
}

.form-desc {
  margin-bottom: 30px;
  color: #666;
  line-height: 1.6;
}

/* 地图部分 */
.map-section {
  background-color: #f9f9f9;
  padding: 80px 0;
}

.map-container {
  height: 400px;
  margin-top: 40px;
  border-radius: 8px;
  overflow: hidden;
}

.map-placeholder {
  height: 100%;
  background-color: #e0e0e0;
  display: flex;
  align-items: center;
  justify-content: center;
  color: #666;
  font-size: 18px;
}

/* 常见问题部分 */
.faq-section {
  padding: 80px 0;
}

.faq-list {
  max-width: 800px;
  margin: 40px auto 0;
}

/* 响应式调整 */
@media (max-width: 768px) {
  .page-title {
    font-size: 36px;
  }
  
  .page-subtitle {
    font-size: 18px;
  }
  
  .contact-content {
    flex-direction: column;
  }
  
  .map-container {
    height: 300px;
  }
}
</style>