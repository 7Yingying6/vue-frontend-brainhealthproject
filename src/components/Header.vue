<template>
  <header class="header">
    <div class="container">
      <!-- Desktop Navigation -->
      <nav class="desktop-nav">
        <div class="logo">
          <img src="@/assets/images/logo-icon.svg" alt="VitaminD Brain Logo" class="logo-icon">
          <span class="logo-text">VitaminD Brain</span>
        </div>
        <ul class="nav-menu">
          <li><a href="#" class="nav-link active"><img src="@/assets/images/home-icon.svg" alt="Home"><span>Home</span></a></li>
          <li><a href="#" class="nav-link"><img src="@/assets/images/sun-icon.svg" alt="Sun"><span>Sun Exposure</span></a></li>
          <li><a href="#" class="nav-link"><img src="@/assets/images/food-icon.svg" alt="Food"><span>Food Intake</span></a></li>
          <li><a href="#" class="nav-link"><img src="@/assets/images/insights-icon.svg" alt="Insights"><span>Insights</span></a></li>
          <li><a href="#" class="nav-link"><img src="@/assets/images/garden-icon.svg" alt="Garden"><span>Garden</span></a></li>
          <li><a href="#" class="nav-link"><img src="@/assets/images/health-progress-icon.svg" alt="Health Progress"><span>Health Progress</span></a></li>
          <li><a href="#" class="nav-link"><img src="@/assets/images/health-info-icon.svg" alt="Health Info"><span>Health Info</span></a></li>
        </ul>
      </nav>

      <!-- Mobile Navigation -->
      <nav class="mobile-nav">
        <div class="logo">
          <img src="@/assets/images/logo-icon.svg" alt="VitaminD Brain Logo" class="logo-icon">
          <span class="logo-text">VitaminD Brain</span>
        </div>
        <button class="hamburger" @click="toggleMobileMenu" :class="{ active: isMobileMenuOpen }">
          <span></span>
          <span></span>
          <span></span>
        </button>
      </nav>

      <!-- Mobile Menu -->
      <div class="mobile-menu" :class="{ active: isMobileMenuOpen }">
        <ul class="mobile-nav-menu">
          <li><a href="#" class="nav-link active" @click="closeMobileMenu"><img src="@/assets/images/home-icon.svg" alt="Home">Home</a></li>
          <li><a href="#" class="nav-link" @click="closeMobileMenu"><img src="@/assets/images/sun-icon.svg" alt="Sun">Sun Exposure</a></li>
          <li><a href="#" class="nav-link" @click="closeMobileMenu"><img src="@/assets/images/food-icon.svg" alt="Food">Food Intake</a></li>
          <li><a href="#" class="nav-link" @click="closeMobileMenu"><img src="@/assets/images/insights-icon.svg" alt="Insights">Insights</a></li>
          <li><a href="#" class="nav-link" @click="closeMobileMenu"><img src="@/assets/images/garden-icon.svg" alt="Garden">Garden</a></li>
          <li><a href="#" class="nav-link" @click="closeMobileMenu"><img src="@/assets/images/health-progress-icon.svg" alt="Health Progress">Health Progress</a></li>
          <li><a href="#" class="nav-link" @click="closeMobileMenu"><img src="@/assets/images/health-info-icon.svg" alt="Health Info">Health Info</a></li>
        </ul>
      </div>
    </div>
  </header>
</template>

<script>
export default {
  name: 'Header',
  data() {
    return {
      isMobileMenuOpen: false
    }
  },
  methods: {
    toggleMobileMenu() {
      this.isMobileMenuOpen = !this.isMobileMenuOpen
    },
    closeMobileMenu() {
      this.isMobileMenuOpen = false
    }
  }
}
</script>

<style scoped>
.header {
  background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
  padding: 1rem 0;
  position: sticky;
  top: 0;
  z-index: 1000;
  box-shadow: 0 2px 10px rgba(0, 0, 0, 0.1);
}

.container {
  max-width: 1200px;
  margin: 0 auto;
  padding: 0 2rem;
  position: relative;
}

.desktop-nav {
  display: flex;
  justify-content: space-between;
  align-items: center;
}

.logo {
  display: flex;
  align-items: center;
  gap: 0.5rem;
}

.logo-icon {
  width: 40px;
  height: 40px;
}

.logo-text {
  font-size: 1.5rem;
  font-weight: bold;
  color: white;
}

.nav-menu {
  display: flex;
  list-style: none;
  margin: 0;
  padding: 0;
  gap: 1rem;
}

.nav-link {
  display: flex;
  align-items: center;
  gap: 0.3rem;
  color: white;
  text-decoration: none;
  padding: 0.4rem 0.8rem;
  border-radius: 20px;
  transition: all 0.3s ease;
  font-weight: 500;
  font-size: 0.9rem;
}

.nav-link:hover,
.nav-link.active {
  background: rgba(255, 255, 255, 0.2);
  transform: translateY(-1px);
}

.nav-link img {
  width: 16px;
  height: 16px;
  filter: brightness(0) invert(1);
}

.nav-link span {
  white-space: nowrap;
}

/* Mobile Navigation */
.mobile-nav {
  display: none;
  justify-content: space-between;
  align-items: center;
}

.hamburger {
  display: flex;
  flex-direction: column;
  gap: 4px;
  background: none;
  border: none;
  cursor: pointer;
  padding: 8px;
}

.hamburger span {
  width: 25px;
  height: 3px;
  background: white;
  transition: all 0.3s ease;
  border-radius: 2px;
}

.hamburger.active span:nth-child(1) {
  transform: rotate(45deg) translate(5px, 5px);
}

.hamburger.active span:nth-child(2) {
  opacity: 0;
}

.hamburger.active span:nth-child(3) {
  transform: rotate(-45deg) translate(7px, -6px);
}

.mobile-menu {
  position: absolute;
  top: 100%;
  left: 0;
  right: 0;
  background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
  transform: translateY(-100%);
  opacity: 0;
  visibility: hidden;
  transition: all 0.3s ease;
  border-radius: 0 0 15px 15px;
  box-shadow: 0 5px 15px rgba(0, 0, 0, 0.2);
}

.mobile-menu.active {
  transform: translateY(0);
  opacity: 1;
  visibility: visible;
}

.mobile-nav-menu {
  list-style: none;
  margin: 0;
  padding: 1rem;
}

.mobile-nav-menu li {
  margin-bottom: 0.5rem;
}

.mobile-nav-menu .nav-link {
  display: flex;
  align-items: center;
  gap: 1rem;
  padding: 1rem;
  border-radius: 10px;
  width: 100%;
  box-sizing: border-box;
}

/* Responsive Design */
@media (max-width: 768px) {
  .desktop-nav {
    display: none;
  }
  
  .mobile-nav {
    display: flex;
  }
  
  .container {
    padding: 0 1rem;
  }
  
  .logo-text {
    font-size: 1.2rem;
  }
  
  .logo-icon {
    width: 35px;
    height: 35px;
  }
}

@media (max-width: 480px) {
  .logo-text {
    font-size: 1rem;
  }
  
  .logo-icon {
    width: 30px;
    height: 30px;
  }
}
</style>