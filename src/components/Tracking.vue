<template>
  <section class="tracking-section">
    <div class="container">
      <div class="section-header">
        <h2 class="section-title">Comprehensive Vitamin D Tracking</h2>
        <p class="section-description">
          Our website helps middle-aged Australians who work indoors monitor and improve their vitamin D levels for better brain health and cognitive protection.
        </p>
      </div>
      <div class="tracking-cards">
        <div class="tracking-card orange">
          <div class="card-icon orange-icon">
            <img :src="sunIcon" alt="Sun Icon" />
          </div>
          <h3>Sun Exposure Tracking</h3>
          <p>Monitor your daily safe sun exposure for optimal vitamin D production</p>
        </div>
        
        <div class="tracking-card green">
          <div class="card-icon green-icon">
            <img :src="foodIcon" alt="Food Icon" />
          </div>
          <h3>Nutrition Tracking</h3>
          <p>Log vitamin D-rich foods and track your daily intake in IU</p>
        </div>
        
        <div class="tracking-card blue">
          <div class="card-icon blue-icon">
            <img :src="brainIcon" alt="Brain Icon" />
          </div>
          <h3>Brain Health Insights</h3>
          <p>Learn how vitamin D protects your brain and cognitive function</p>
        </div>
        
        <div class="tracking-card purple">
          <div class="card-icon purple-icon">
            <img :src="gardenIcon" alt="Garden Icon" />
          </div>
          <h3>Virtual Garden</h3>
          <p>Grow your virtual garden as you maintain healthy vitamin D habits</p>
        </div>
      </div>
    </div>
  </section>
</template>

<script>
import sunIcon from '@/assets/images/sun-icon.svg'
import foodIcon from '@/assets/images/food-icon.svg'
import brainIcon from '@/assets/images/brain-icon.svg'
import gardenIcon from '@/assets/images/garden-icon.svg'

export default {
  name: 'Tracking',
  data() {
    return {
      sunIcon,
      foodIcon,
      brainIcon,
      gardenIcon
    }
  }
}
</script>

<style scoped>
.tracking-section {
  background: linear-gradient(135deg, #ffffff 0%, #f9fafb 50%, #f0fdf4 100%);
  padding: 80px 0;
}

.container {
  max-width: 1200px;
  margin: 0 auto;
  padding: 0 20px;
}

.section-header {
  text-align: center;
  margin-bottom: 60px;
}

.section-title {
  font-size: 2.5rem;
  font-weight: bold;
  color: #2d3748;
  margin-bottom: 1rem;
}

.section-description {
  font-size: 1.125rem;
  color: #6b7280;
  max-width: 600px;
  margin: 0 auto;
  line-height: 1.6;
}

.tracking-cards {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));
  gap: 24px;
  align-items: start;
}

.tracking-card {
  padding: 32px 24px;
  border-radius: 12px;
  text-align: left;
  transition: transform 0.3s ease, box-shadow 0.3s ease;
  height: 100%;
  display: flex;
  flex-direction: column;
}

.tracking-card:hover {
  transform: translateY(-6px);
  box-shadow: 0 12px 30px rgba(199, 238, 208, 0.3);
}

.tracking-card.orange {
  background: linear-gradient(135deg, #fef3c7 0%, #fde68a 100%);
  border: 1px solid #f59e0b;
}

.tracking-card.green {
  background: linear-gradient(135deg, #dcfce7 0%, #bbf7d0 100%);
  border: 1px solid #22c55e;
}

.tracking-card.blue {
  background: linear-gradient(135deg, #dbeafe 0%, #bfdbfe 100%);
  border: 1px solid #3b82f6;
}

.tracking-card.purple {
  background: linear-gradient(135deg, #f3e8ff 0%, #e9d5ff 100%);
  border: 1px solid #8b5cf6;
}

.card-icon {
  width: 48px;
  height: 48px;
  border-radius: 50%;
  display: flex;
  align-items: center;
  justify-content: center;
  margin-bottom: 20px;
}

.card-icon img {
  width: 24px;
  height: 24px;
}

.orange-icon {
  background: linear-gradient(135deg, #f59e0b 0%, #d97706 100%);
  color: white;
  box-shadow: 0 4px 12px rgba(245, 158, 11, 0.3);
}

.green-icon {
  background: linear-gradient(135deg, #22c55e 0%, #16a34a 100%);
  color: white;
  box-shadow: 0 4px 12px rgba(34, 197, 94, 0.3);
}

.blue-icon {
  background: linear-gradient(135deg, #3b82f6 0%, #2563eb 100%);
  color: white;
  box-shadow: 0 4px 12px rgba(59, 130, 246, 0.3);
}

.purple-icon {
  background: linear-gradient(135deg, #8b5cf6 0%, #7c3aed 100%);
  color: white;
  box-shadow: 0 4px 12px rgba(139, 92, 246, 0.3);
}

.tracking-card h3 {
  font-size: 20px;
  font-weight: 600;
  color: #1f2937;
  margin-bottom: 12px;
  line-height: 1.3;
}

.tracking-card p {
  font-size: 14px;
  color: #6b7280;
  line-height: 1.5;
  margin: 0;
}

/* Responsive design */
@media (max-width: 768px) {
  .tracking-section {
    padding: 60px 0;
  }
  
  .container {
    padding: 0 16px;
  }
  
  .tracking-cards {
    grid-template-columns: 1fr;
    gap: 20px;
  }
  
  .tracking-card {
    padding: 24px 20px;
  }
  
  .tracking-card h3 {
    font-size: 18px;
  }
}

@media (max-width: 480px) {
  .tracking-section {
    padding: 40px 0;
  }
  
  .tracking-card {
    padding: 20px 16px;
  }
  
  .card-icon {
    width: 40px;
    height: 40px;
    margin-bottom: 16px;
  }
  
  .card-icon img {
    width: 20px;
    height: 20px;
  }
  
  .tracking-card h3 {
    font-size: 16px;
  }
  
  .tracking-card p {
    font-size: 13px;
  }
}
</style>