<template>
  <div class="sun-exposure-page">
    <Header />
    <main class="main-content">
      <div class="container">
        <!-- Title Section -->
        <div class="title-section">
          <h1 class="page-title">Sun Exposure Tracker</h1>
          <p class="page-description">
            Monitor your daily safe sun exposure for optimal vitamin D production with
            <span class="highlight">personalized weather-based recommendations</span>
          </p>
        </div>

        <!-- Today's Vitamin D Helper Card -->
        <div class="helper-card">
          <div class="helper-header">
            <div class="helper-icon">
              <svg width="24" height="24" viewBox="0 0 24 24" fill="none">
                <circle cx="12" cy="12" r="5" stroke="#f59e0b" stroke-width="2" fill="#fbbf24"/>
                <path d="M12 1v2m0 18v2M4.22 4.22l1.42 1.42m12.72 12.72l1.42 1.42M1 12h2m18 0h2M4.22 19.78l1.42-1.42M18.36 5.64l1.42-1.42" stroke="#f59e0b" stroke-width="2"/>
              </svg>
            </div>
            <h2 class="helper-title">Today's Vitamin D Helper</h2>
          </div>
          
          <div class="helper-content">
            <!-- Location Card -->
            <div class="location-card">
              <div class="location-header">
                <div class="location-icon">
                  <svg width="16" height="16" viewBox="0 0 24 24" fill="none">
                    <path d="M21 10c0 7-9 13-9 13s-9-6-9-13a9 9 0 0 1 18 0z" stroke="#ef4444" stroke-width="2" fill="#ef4444"/>
                    <circle cx="12" cy="10" r="3" stroke="white" stroke-width="2" fill="white"/>
                  </svg>
                </div>
                <span class="location-text">Melbourne, Victoria</span>
              </div>
              
              <div class="weather-info">
                <div class="weather-item">
                  <span class="weather-label">Temperature:</span>
                  <span class="weather-value">22°C</span>
                </div>
                <div class="weather-item">
                  <span class="weather-label">Weather:</span>
                  <span class="weather-value">Partly Cloudy</span>
                </div>
              </div>
            </div>

            <!-- UV Index Card -->
            <div class="uv-card">
              <div class="uv-header">
                <h3 class="uv-title">Current UV Index</h3>
                <div class="uv-value">6</div>
              </div>
              <div class="uv-level high">High</div>
              <p class="uv-description">
                Catch the sunshine for a vitamin D top-up &#9728;&#65039;&#128155;, but give your skin some love with protection after 15&ndash;20 minutes.
              </p>
            </div>

            <!-- Best Time Today -->
            <div class="best-time-card">
              <div class="best-time-header">
                <div class="best-time-icon">
                  <svg width="20" height="20" viewBox="0 0 24 24" fill="none">
                    <circle cx="12" cy="12" r="10" stroke="#3b82f6" stroke-width="2" fill="none"/>
                    <polyline points="12,6 12,12 16,14" stroke="#3b82f6" stroke-width="2"/>
                  </svg>
                </div>
                <h3 class="best-time-title">Best Time Today</h3>
              </div>
              <div class="best-time-content">
                <div class="time-range">10:00 AM - 2:00 PM</div>
                <div class="time-description">Autumn sun is gentler - perfect for longer exposure sessions</div>
              </div>
            </div>

            <!-- Recommended Exposure Times -->
            <div class="exposure-times">
              <h3 class="exposure-title">Recommended Safe Exposure Times</h3>
              <div class="skin-types">
                <div class="skin-type">
                  <div class="skin-color light"></div>
                  <div class="skin-info">
                    <span class="skin-label">Light Skin</span>
                    <span class="skin-time">10-15 minutes</span>
                  </div>
                </div>
                <div class="skin-type">
                  <div class="skin-color medium"></div>
                  <div class="skin-info">
                    <span class="skin-label">Medium Skin</span>
                    <span class="skin-time">15-20 minutes</span>
                  </div>
                </div>
                <div class="skin-type">
                  <div class="skin-color dark"></div>
                  <div class="skin-info">
                    <span class="skin-label">Dark Skin</span>
                    <span class="skin-time">20-30 minutes</span>
                  </div>
                </div>
              </div>
            </div>

            <!-- Sun Exposure Timer -->
            <div class="timer-section">
              <h3 class="timer-title">Sun Exposure Timer</h3>
              <div class="timer-card">
                <div class="timer-display">
                  <span class="timer-time">{{ formatTime(currentTime) }}</span>
                  <span class="timer-label">{{ timerStatus }}</span>
                </div>
                <div class="timer-controls">
                  <button 
                    class="timer-btn start" 
                    @click="startTimer"
                    :disabled="isRunning"
                  >
                    Start
                  </button>
                  <button 
                    class="timer-btn pause" 
                    @click="pauseTimer"
                    :disabled="!isRunning"
                  >
                    Pause
                  </button>
                  <button 
                    class="timer-btn reset" 
                    @click="resetTimer"
                  >
                    Reset
                  </button>
                </div>
              </div>
            </div>
          </div>
        </div>
      </div>

    <!-- Sun Exposure History & Stats Section -->
    <div class="history-stats-section">
      <div class="container">
        <div class="section-header">
          <div class="section-title-with-icon">
            <svg width="24" height="24" viewBox="0 0 24 24" fill="none" xmlns="http://www.w3.org/2000/svg">
              <rect x="3" y="4" width="18" height="18" rx="2" ry="2" stroke="#dc2626" stroke-width="2" fill="none"/>
              <line x1="16" y1="2" x2="16" y2="6" stroke="#dc2626" stroke-width="2"/>
              <line x1="8" y1="2" x2="8" y2="6" stroke="#dc2626" stroke-width="2"/>
              <line x1="3" y1="10" x2="21" y2="10" stroke="#dc2626" stroke-width="2"/>
            </svg>
            <h2 class="section-title">Sun Exposure History & Stats</h2>
          </div>
        </div>

        <!-- Stats Cards -->
        <div class="stats-grid">
          <div class="stat-card green">
            <div class="stat-label">This Week</div>
            <div class="stat-value">5</div>
            <div class="stat-unit">sessions</div>
          </div>
          <div class="stat-card blue">
            <div class="stat-label">Weekly Avg</div>
            <div class="stat-value">18</div>
            <div class="stat-unit">minutes</div>
          </div>
          <div class="stat-card purple">
            <div class="stat-label">Total Points</div>
            <div class="stat-value">140</div>
            <div class="stat-unit">earned</div>
          </div>
          <div class="stat-card orange">
            <div class="stat-label">Current Streak</div>
            <div class="stat-value">7</div>
            <div class="stat-unit">days</div>
          </div>
        </div>

        <!-- Recent Sessions -->
        <div class="recent-sessions">
          <h3 class="sessions-title">Recent Sessions</h3>
          <div class="sessions-list">
            <div class="session-item completed">
              <div class="session-indicator"></div>
              <div class="session-info">
                <div class="session-date">Mon, 15 Jan</div>
                <div class="session-duration">20 minutes</div>
              </div>
              <div class="session-status completed-status">Completed</div>
            </div>
            <div class="session-item completed">
              <div class="session-indicator"></div>
              <div class="session-info">
                <div class="session-date">Sun, 14 Jan</div>
                <div class="session-duration">15 minutes</div>
              </div>
              <div class="session-status completed-status">Completed</div>
            </div>
            <div class="session-item completed">
              <div class="session-indicator"></div>
              <div class="session-info">
                <div class="session-date">Sat, 13 Jan</div>
                <div class="session-duration">25 minutes</div>
              </div>
              <div class="session-status completed-status">Completed</div>
            </div>
            <div class="session-item incomplete">
              <div class="session-indicator"></div>
              <div class="session-info">
                <div class="session-date">Fri, 12 Jan</div>
                <div class="session-duration">18 minutes</div>
              </div>
              <div class="session-status incomplete-status">Incomplete</div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </main>
  </div>
</template>

<script>
import Header from '@/components/Header.vue'

export default {
  name: 'SunExposureView',
  components: {
    Header
  },
  data() {
    return {
      currentTime: 0, // in seconds
      isRunning: false,
      timer: null
    }
  },
  computed: {
    timerStatus() {
      if (this.isRunning) {
        return 'Timer Running'
      } else if (this.currentTime > 0) {
        return 'Timer Paused'
      } else {
        return 'Ready to Start'
      }
    }
  },
  methods: {
    formatTime(seconds) {
      const mins = Math.floor(seconds / 60)
      const secs = seconds % 60
      return `${mins.toString().padStart(2, '0')}:${secs.toString().padStart(2, '0')}`
    },
    startTimer() {
      this.isRunning = true
      this.timer = setInterval(() => {
        this.currentTime++
      }, 1000)
    },
    pauseTimer() {
      this.isRunning = false
      if (this.timer) {
        clearInterval(this.timer)
        this.timer = null
      }
    },
    resetTimer() {
      this.isRunning = false
      this.currentTime = 0
      if (this.timer) {
        clearInterval(this.timer)
        this.timer = null
      }
    }
  },
  beforeUnmount() {
    if (this.timer) {
      clearInterval(this.timer)
    }
  }
}
</script>

<style scoped>
.sun-exposure-page {
  min-height: 100vh;
  background: linear-gradient(135deg, #f0fdf4 0%, #ecfdf5 100%);
}

.main-content {
  padding: 2rem 0;
}

.container {
  max-width: 1200px;
  margin: 0 auto;
  padding: 0 2rem;
}

.title-section {
  text-align: center;
  margin-bottom: 3rem;
}

.page-title {
  font-size: 3rem;
  font-weight: bold;
  color: #2d3748;
  margin-bottom: 1rem;
  line-height: 1.2;
}

.page-description {
  font-size: 1.125rem;
  color: #6b7280;
  max-width: 600px;
  margin: 0 auto;
  line-height: 1.6;
}

.highlight {
  color: #16a34a;
  font-weight: 600;
}

.helper-card {
  background: linear-gradient(135deg, #fef3c7 0%, #fde68a 100%);
  border-radius: 12px;
  padding: 2rem;
  box-shadow: 0 8px 25px rgba(245, 158, 11, 0.15);
  border: 1px solid #f59e0b;
}

.helper-header {
  display: flex;
  align-items: center;
  gap: 1rem;
  margin-bottom: 2rem;
}

.helper-icon {
  display: flex;
  align-items: center;
  justify-content: center;
}

.helper-title {
  font-size: 1.5rem;
  font-weight: 600;
  color: #92400e;
  margin: 0;
}

.helper-content {
  display: grid;
  gap: 2rem;
}

.location-card {
  background: white;
  border-radius: 8px;
  padding: 1.5rem;
  box-shadow: 0 4px 12px rgba(0, 0, 0, 0.1);
}

.location-header {
  display: flex;
  align-items: center;
  gap: 0.5rem;
  margin-bottom: 1rem;
}

.location-icon {
  display: flex;
  align-items: center;
}

.location-text {
  font-weight: 600;
  color: #2d3748;
}

.weather-info {
  display: grid;
  gap: 0.5rem;
}

.weather-item {
  display: flex;
  justify-content: space-between;
  align-items: center;
}

.weather-label {
  color: #6b7280;
  font-size: 0.875rem;
}

.weather-value {
  font-weight: 600;
  color: #2d3748;
}

.uv-card {
  background: white;
  border-radius: 8px;
  padding: 1.5rem;
  box-shadow: 0 4px 12px rgba(0, 0, 0, 0.1);
}

.uv-header {
  display: flex;
  justify-content: space-between;
  align-items: center;
  margin-bottom: 1rem;
}

.uv-title {
  font-size: 1.125rem;
  font-weight: 600;
  color: #2d3748;
  margin: 0;
}

.uv-value {
  font-size: 2rem;
  font-weight: bold;
  color: #f59e0b;
}

.uv-level {
  display: inline-block;
  padding: 0.25rem 0.75rem;
  border-radius: 20px;
  font-size: 0.875rem;
  font-weight: 600;
  margin-bottom: 1rem;
}

.uv-level.high {
  background-color: #fef3c7;
  color: #92400e;
}

.uv-description {
  color: #6b7280;
  font-size: 0.875rem;
  line-height: 1.5;
  margin: 0;
}

.best-time-card {
  background: linear-gradient(135deg, #eff6ff 0%, #dbeafe 100%);
  border: 1px solid #dbeafe;
  border-radius: 12px;
  padding: 1.5rem;
  margin-bottom: 1.5rem;
  transition: all 0.3s cubic-bezier(0.4, 0, 0.2, 1);
  cursor: pointer;
  position: relative;
  overflow: hidden;
}

.best-time-card::before {
  content: '';
  position: absolute;
  top: 0;
  left: -100%;
  width: 100%;
  height: 100%;
  background: linear-gradient(90deg, transparent, rgba(255, 255, 255, 0.4), transparent);
  transition: left 0.6s ease;
}

.best-time-card:hover {
  transform: translateY(-2px);
  box-shadow: 0 8px 25px rgba(59, 130, 246, 0.15);
  border-color: #93c5fd;
  background: linear-gradient(135deg, #dbeafe 0%, #bfdbfe 100%);
}

.best-time-card:hover::before {
  left: 100%;
}

.best-time-header {
  display: flex;
  align-items: center;
  gap: 0.75rem;
  margin-bottom: 1rem;
}

.best-time-icon {
  display: flex;
  align-items: center;
  justify-content: center;
  transition: transform 0.3s ease;
}

.best-time-card:hover .best-time-icon {
  transform: rotate(360deg);
}

.best-time-title {
  font-size: 1.125rem;
  font-weight: 600;
  color: #3b82f6;
  margin: 0;
}

.best-time-content {
  text-align: center;
}

.time-range {
  font-size: 1.5rem;
  font-weight: bold;
  color: #3b82f6;
  margin-bottom: 0.5rem;
  transition: all 0.3s ease;
}

.best-time-card:hover .time-range {
  transform: scale(1.05);
  color: #1d4ed8;
}

.time-description {
  color: #6b7280;
  font-size: 0.875rem;
  line-height: 1.5;
}

.exposure-times {
  background: white;
  border-radius: 8px;
  padding: 1.5rem;
  box-shadow: 0 4px 12px rgba(0, 0, 0, 0.1);
}

.exposure-title {
  font-size: 1.125rem;
  font-weight: 600;
  color: #2d3748;
  margin: 0 0 1.5rem 0;
}

.skin-types {
  display: grid;
  gap: 1rem;
}

.skin-type {
  display: flex;
  align-items: center;
  gap: 1rem;
  padding: 1rem;
  background: #f9fafb;
  border-radius: 8px;
}

.skin-color {
  width: 40px;
  height: 40px;
  border-radius: 50%;
  border: 2px solid #e5e7eb;
}

.skin-color.light {
  background: #fde68a;
}

.skin-color.medium {
  background: #d97706;
}

.skin-color.dark {
  background: #92400e;
}

.skin-info {
  display: flex;
  flex-direction: column;
  gap: 0.25rem;
}

.skin-label {
  font-weight: 600;
  color: #2d3748;
}

.skin-time {
  color: #16a34a;
  font-weight: 600;
}

.timer-section {
  background: white;
  border-radius: 8px;
  padding: 1.5rem;
  box-shadow: 0 4px 12px rgba(0, 0, 0, 0.1);
}

.timer-title {
  font-size: 1.125rem;
  font-weight: 600;
  color: #2d3748;
  margin: 0 0 1.5rem 0;
}

.timer-card {
  text-align: center;
}

.timer-display {
  margin-bottom: 2rem;
}

.timer-time {
  display: block;
  font-size: 3rem;
  font-weight: bold;
  color: #16a34a;
  margin-bottom: 0.5rem;
}

.timer-label {
  color: #6b7280;
  font-size: 0.875rem;
}

.timer-controls {
  display: flex;
  gap: 1rem;
  justify-content: center;
}

.timer-btn {
  padding: 0.75rem 1.5rem;
  border-radius: 12px;
  border: none;
  font-weight: 600;
  cursor: pointer;
  transition: all 0.4s cubic-bezier(0.4, 0, 0.2, 1);
  position: relative;
  overflow: hidden;
  box-shadow: 0 4px 15px rgba(0, 0, 0, 0.1);
  transform: translateY(0);
}

.timer-btn::before {
  content: '';
  position: absolute;
  top: 0;
  left: -100%;
  width: 100%;
  height: 100%;
  background: linear-gradient(90deg, transparent, rgba(255, 255, 255, 0.3), transparent);
  transition: left 0.6s;
}

.timer-btn:hover::before {
  left: 100%;
}

.timer-btn:disabled {
  opacity: 0.5;
  cursor: not-allowed;
  transform: none;
}

.timer-btn:disabled::before {
  display: none;
}

.timer-btn.start {
  background: linear-gradient(135deg, #d5e5a9 0%, #c8dd7a 100%);
  color: #4a5d23;
  box-shadow: 0 4px 15px rgba(213, 229, 169, 0.4);
}

.timer-btn.start:hover:not(:disabled) {
  background: linear-gradient(135deg, #c8dd7a 0%, #b8d154 100%);
  transform: translateY(-2px);
  box-shadow: 0 8px 25px rgba(213, 229, 169, 0.6);
}

.timer-btn.start:active:not(:disabled) {
  transform: translateY(0);
  box-shadow: 0 4px 15px rgba(213, 229, 169, 0.4);
}

.timer-btn.pause {
  background: linear-gradient(135deg, #fbebba 0%, #f5d982 100%);
  color: #8b6914;
  box-shadow: 0 4px 15px rgba(251, 235, 186, 0.4);
}

.timer-btn.pause:hover:not(:disabled) {
  background: linear-gradient(135deg, #f5d982 0%, #efc441 100%);
  transform: translateY(-2px);
  box-shadow: 0 8px 25px rgba(251, 235, 186, 0.6);
}

.timer-btn.pause:active:not(:disabled) {
  transform: translateY(0);
  box-shadow: 0 4px 15px rgba(251, 235, 186, 0.4);
}

.timer-btn.reset {
  background: linear-gradient(135deg, #f9d8d1 0%, #f4b5a8 100%);
  color: #8b3a2e;
  box-shadow: 0 4px 15px rgba(249, 216, 209, 0.4);
}

.timer-btn.reset:hover:not(:disabled) {
  background: linear-gradient(135deg, #f4b5a8 0%, #ee9284 100%);
  transform: translateY(-2px);
  box-shadow: 0 8px 25px rgba(249, 216, 209, 0.6);
}

.timer-btn.reset:active:not(:disabled) {
  transform: translateY(0);
  box-shadow: 0 4px 15px rgba(249, 216, 209, 0.4);
}

/* Responsive Design */
@media (max-width: 768px) {
  .main-content {
    padding: 1rem 0;
  }
  
  .container {
    padding: 0 1rem;
  }
  
  .page-title {
    font-size: 2rem;
  }
  
  .page-description {
    font-size: 1rem;
  }
  
  .helper-card {
    padding: 1.5rem;
  }
  
  .helper-header {
    flex-direction: column;
    text-align: center;
    gap: 0.5rem;
  }
  
  .timer-controls {
    flex-direction: column;
    align-items: center;
  }
  
  .timer-btn {
    width: 100%;
    max-width: 200px;
  }
  
  .timer-time {
    font-size: 2rem;
  }
}

/* History & Stats Section */
.history-stats-section {
  background: linear-gradient(135deg, #f9fafb 0%, #f3f4f6 100%);
  padding: 3rem 0;
  margin-top: 2rem;
}

.section-title-with-icon {
  display: flex;
  align-items: center;
  gap: 0.75rem;
  justify-content: center;
  margin-bottom: 2rem;
}

.section-title {
  font-size: 1.5rem;
  font-weight: 600;
  color: #dc2626;
  margin: 0;
}

.stats-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
  gap: 1.5rem;
  margin-bottom: 3rem;
}

.stat-card {
  background: white;
  border-radius: 12px;
  padding: 1.5rem;
  text-align: center;
  box-shadow: 0 4px 12px rgba(0, 0, 0, 0.1);
  transition: transform 0.3s ease, box-shadow 0.3s ease;
}

.stat-card:hover {
  transform: translateY(-2px);
  box-shadow: 0 8px 25px rgba(0, 0, 0, 0.15);
}

.stat-card.green {
  border-left: 4px solid #22c55e;
  background: linear-gradient(135deg, #dcfce7 0%, #bbf7d0 100%);
}

.stat-card.blue {
  border-left: 4px solid #3b82f6;
  background: linear-gradient(135deg, #dbeafe 0%, #bfdbfe 100%);
}

.stat-card.purple {
  border-left: 4px solid #8b5cf6;
  background: linear-gradient(135deg, #f3e8ff 0%, #e9d5ff 100%);
}

.stat-card.orange {
  border-left: 4px solid #f59e0b;
  background: linear-gradient(135deg, #fef3c7 0%, #fde68a 100%);
}

.stat-label {
  font-size: 0.875rem;
  color: #6b7280;
  margin-bottom: 0.5rem;
  font-weight: 500;
}

.stat-value {
  font-size: 2.5rem;
  font-weight: bold;
  margin-bottom: 0.25rem;
}

.stat-card.green .stat-value {
  color: #16a34a;
}

.stat-card.blue .stat-value {
  color: #2563eb;
}

.stat-card.purple .stat-value {
  color: #7c3aed;
}

.stat-card.orange .stat-value {
  color: #d97706;
}

.stat-unit {
  font-size: 0.875rem;
  color: #6b7280;
  font-weight: 500;
}

/* Recent Sessions */
.recent-sessions {
  background: white;
  border-radius: 12px;
  padding: 2rem;
  box-shadow: 0 4px 12px rgba(0, 0, 0, 0.1);
}

.sessions-title {
  font-size: 1.25rem;
  font-weight: 600;
  color: #2d3748;
  margin-bottom: 1.5rem;
}

.sessions-list {
  display: flex;
  flex-direction: column;
  gap: 1rem;
}

.session-item {
  display: flex;
  align-items: center;
  padding: 1rem;
  border-radius: 8px;
  transition: background-color 0.3s ease;
}

.session-item.completed {
  background: linear-gradient(135deg, #f0fdf4 0%, #dcfce7 100%);
}

.session-item.incomplete {
  background: linear-gradient(135deg, #fef2f2 0%, #fecaca 100%);
}

.session-indicator {
  width: 12px;
  height: 12px;
  border-radius: 50%;
  margin-right: 1rem;
  flex-shrink: 0;
}

.session-item.completed .session-indicator {
  background: #22c55e;
}

.session-item.incomplete .session-indicator {
  background: #6b7280;
}

.session-info {
  flex: 1;
}

.session-date {
  font-weight: 600;
  color: #2d3748;
  margin-bottom: 0.25rem;
}

.session-duration {
  font-size: 0.875rem;
  color: #6b7280;
}

.session-status {
  padding: 0.375rem 0.75rem;
  border-radius: 20px;
  font-size: 0.75rem;
  font-weight: 600;
  text-transform: uppercase;
  letter-spacing: 0.05em;
}

.completed-status {
  background: #22c55e;
  color: white;
}

.incomplete-status {
  background: #6b7280;
  color: white;
}

@media (max-width: 768px) {
  .history-stats-section {
    padding: 2rem 0;
  }
  
  .stats-grid {
    grid-template-columns: repeat(2, 1fr);
    gap: 1rem;
  }
  
  .stat-card {
    padding: 1rem;
  }
  
  .stat-value {
    font-size: 2rem;
  }
  
  .recent-sessions {
    padding: 1.5rem;
  }
  
  .session-item {
    padding: 0.75rem;
  }
}

@media (max-width: 480px) {
  .page-title {
    font-size: 1.5rem;
  }
  
  .helper-card {
    padding: 1rem;
  }
  
  .location-card,
  .uv-card,
  .best-time-card,
  .exposure-times,
  .timer-section {
    padding: 1rem;
  }
  
  .time-range {
    font-size: 1.25rem;
  }
  
  .skin-type {
    padding: 0.75rem;
  }
  
  .skin-color {
    width: 30px;
    height: 30px;
  }
  
  .stats-grid {
    grid-template-columns: 1fr;
  }
  
  .stat-value {
    font-size: 1.75rem;
  }
  
  .section-title {
    font-size: 1.25rem;
  }
}
</style>