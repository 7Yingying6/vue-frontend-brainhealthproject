<template>
  <section class="tracking-section">
    <div class="container">
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
  background-color: #ffffff;
  padding: 80px 0;
}

.container {
  max-width: 1200px;
  margin: 0 auto;
  padding: 0 20px;
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
  transform: translateY(-4px);
  box-shadow: 0 8px 25px rgba(0, 0, 0, 0.1);
}

.tracking-card.orange {
  background-color: #fff7ed;
}

.tracking-card.green {
  background-color: #f0fdf4;
}

.tracking-card.blue {
  background-color: #eff6ff;
}

.tracking-card.purple {
  background-color: #faf5ff;
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
  background-color: #f97316;
}

.green-icon {
  background-color: #22c55e;
}

.blue-icon {
  background-color: #3b82f6;
}

.purple-icon {
  background-color: #a855f7;
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