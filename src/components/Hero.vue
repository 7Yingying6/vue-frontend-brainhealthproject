<template>
  <section class="hero">
    <div class="container">
      <div class="hero-content">
        <div class="hero-text">
          <h1 class="hero-title">
            <img src="@/assets/images/brain-icon.svg" alt="Brain" class="brain-icon">
            Test Your Vitamin D Level
          </h1>
          <p class="hero-subtitle">
            Discover your vitamin D status and get personalized recommendations for optimal health.
            <br>
            &bull; Quick and easy testing
            <br>
            &bull; Expert analysis and insights
            <br>
            &bull; Personalized health recommendations
          </p>
          <button class="cta-button">
            Get Started Today
            <span class="button-arrow">&rarr;</span>
          </button>
        </div>
        <div class="hero-image">
          <img src="@/assets/images/hero-image.png" alt="Vitamin D Testing" class="hero-img">
        </div>
      </div>
    </div>
  </section>
</template>

<script>
export default {
  name: 'Hero'
}
</script>

<style scoped>
.hero {
  background: linear-gradient(135deg, #f5f7fa 0%, #c3cfe2 100%);
  padding: 4rem 0;
  min-height: 70vh;
  display: flex;
  align-items: center;
}

.container {
  max-width: 1200px;
  margin: 0 auto;
  padding: 0 2rem;
}

.hero-content {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 4rem;
  align-items: center;
}

.hero-text {
  max-width: 500px;
}

.hero-title {
  font-size: 3rem;
  font-weight: bold;
  color: #2d3748;
  margin-bottom: 1.5rem;
  line-height: 1.2;
  display: flex;
  align-items: center;
  gap: 1rem;
}

.brain-icon {
  width: 60px;
  height: 60px;
  filter: drop-shadow(0 4px 8px rgba(0, 0, 0, 0.1));
}

.hero-subtitle {
  font-size: 1.2rem;
  color: #4a5568;
  margin-bottom: 2rem;
  line-height: 1.6;
}

.cta-button {
  background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
  color: white;
  border: none;
  padding: 1rem 2rem;
  font-size: 1.1rem;
  font-weight: 600;
  border-radius: 50px;
  cursor: pointer;
  transition: all 0.3s ease;
  display: flex;
  align-items: center;
  gap: 0.5rem;
  box-shadow: 0 4px 15px rgba(102, 126, 234, 0.4);
}

.cta-button:hover {
  transform: translateY(-3px);
  box-shadow: 0 8px 25px rgba(102, 126, 234, 0.6);
}

.button-arrow {
  font-size: 1.2rem;
  transition: transform 0.3s ease;
}

.cta-button:hover .button-arrow {
  transform: translateX(5px);
}

.hero-image {
  text-align: center;
}

.hero-img {
  max-width: 100%;
  height: auto;
  border-radius: 20px;
  box-shadow: 0 10px 30px rgba(0, 0, 0, 0.1);
  transition: transform 0.3s ease;
}

.hero-img:hover {
  transform: scale(1.05);
}

/* Responsive Design */
@media (max-width: 768px) {
  .hero {
    padding: 2rem 0;
    min-height: auto;
  }
  
  .container {
    padding: 0 1rem;
  }
  
  .hero-content {
    grid-template-columns: 1fr;
    gap: 2rem;
    text-align: center;
  }
  
  .hero-title {
    font-size: 2rem;
    flex-direction: column;
    gap: 0.5rem;
  }
  
  .brain-icon {
    width: 50px;
    height: 50px;
  }
  
  .hero-subtitle {
    font-size: 1rem;
  }
  
  .cta-button {
    padding: 0.8rem 1.5rem;
    font-size: 1rem;
    justify-content: center;
  }
}

@media (max-width: 480px) {
  .hero-title {
    font-size: 1.5rem;
  }
  
  .brain-icon {
    width: 40px;
    height: 40px;
  }
  
  .hero-subtitle {
    font-size: 0.9rem;
    margin-bottom: 1.5rem;
  }
  
  .cta-button {
    padding: 0.7rem 1.2rem;
    font-size: 0.9rem;
  }
}
</style>