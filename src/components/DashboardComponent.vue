<template>
  <div class="dashboard">
    <Header />

    <div class="main-content">
      <transition name="slide-fade">
        <aside v-if="isSidebarVisible" class="sidebar">
          <h3 class="sidebar-title">Dashboard Menu</h3>
          <ul>
            <li><a @click="scrollToSection('profile')">Profile</a></li>
            <li><router-link to="/Showcase">Showcase</router-link></li>
            <li><router-link to="/Contacts">Contacts</router-link></li>
            <li><router-link to="/resume">Resume</router-link></li>
          </ul>
          <button class="toggle-button hide" @click="toggleSidebar">Hide Sidebar</button>
        </aside>
      </transition>

      <main :class="['dashboard-content', { 'shift-right': !isSidebarVisible }]">
        <button v-if="!isSidebarVisible" class="toggle-button show" @click="toggleSidebar">
          <span class="burger-icon"></span>
          <span class="burger-icon"></span>
          <span class="burger-icon"></span>
        </button>

        <section class="intro-section">
          <h2>Welcome to My Portfolio!</h2>
          <p>
            Hi, I'm Oliver D. De Mesa Jr., from the Technological Institute of the Philippines (TIP), an aspiring professional passionate about hardware and aiming for a career in hardware-related fields.
          </p>
        </section>



        <section id="profile" class="about-section">
          <h3>Profile</h3>
          <div class="about-content">
            <img src="@/assets/profile1.jpg" alt="Profile Picture" class="profile-image" />
            <div class="about-text">
            <strong>Oliver D. De Mesa Jr</strong>
              <br />
              <strong>Birthday:</strong> December 9, 2002  
              <br />
              <strong>Address:</strong> Salawag, Dasmarinas, Cavite  
              <br />
              <strong>Contact Number:</strong> 09081735411  
              <br />
              <strong>Email:</strong> <a href="mailto:modemesajr@tip.edu.ph">modemesajr@tip.edu.ph</a>
              <p>
                Hello! I’m Oliver D. De Mesa Jr., a 21-year-old Computer Engineering student at the Technological Institute of the Philippines (TIP), passionate about hardware and IoT innovations.  
                <br />
              </p>
              <p>
                My interests lie in working with IoT technologies, including NodeMCU and Firebase, to develop impactful solutions. Over the years, I have gained expertise in microcontroller programming, hardware integration, and coding in languages like Python, JavaScript, and Java.  
              </p>
              <p>
                With a detail-oriented approach and a passion for collaboration, I’m eager to contribute to projects that bridge hardware and software to create meaningful impact. Let’s connect and explore how we can innovate together!
              </p>
              <!-- Facebook Logo -->
              <div class="social-container">
                <a href="https://www.facebook.com/demesaoliver10/" target="_blank">
                  <img src="@/assets/fblogo.jpg" alt="Facebook Logo" class="social-logo" />
                </a>
              </div>
            </div>
          </div>
        </section>
      </main>
    </div>

    <Footer />
  </div>
</template>

<script>
import Header from './Header.vue';
import Footer from './Footer.vue';

export default {
  name: 'DashboardComponent',
  components: {
    Header,
    Footer,
  },
  data() {
    return {
      isSidebarVisible: true,
    };
  },
  methods: {
    toggleSidebar() {
      this.isSidebarVisible = !this.isSidebarVisible;
    },
    scrollToSection(sectionId) {
      const section = document.getElementById(sectionId);
      if (section) {
        section.scrollIntoView({ behavior: 'smooth' });
      }
    },
  },
};
</script>

<style scoped>
html {
  scroll-behavior: smooth;
}

.dashboard {
  display: flex;
  flex-direction: column;
  height: 100vh;
}

.main-content {
  display: flex;
  flex: 1;
}

.sidebar {
  width: 250px;
  background-color: #2c3e50;
  color: white;
  padding: 1.5rem;
  display: flex;
  flex-direction: column;
  box-shadow: 2px 0 5px rgba(0, 0, 0, 0.2);
}

.sidebar-title {
  margin-bottom: 1.5rem;
  font-size: 1.5rem;
  font-weight: bold;
}

.sidebar ul {
  list-style: none;
  padding: 0;
}

.sidebar ul li {
  margin: 0.5rem 0;
}

.sidebar ul li a {
  color: white;
  text-decoration: none;
  font-size: 1.1rem;
  padding: 0.5rem 10px;
  border-radius: 5px;
  transition: background-color 0.3s ease;
}

.sidebar ul li a:hover {
  background-color: rgba(255, 255, 255, 0.1);
}

.dashboard-content {
  flex: 1;
  padding: 2rem;
  background-color: #ecf0f1;
  overflow-y: auto;
}

.intro-section,
.about-section {
  margin-top: 2rem;
  background: white;
  padding: 1.5rem;
  border-radius: 8px;
  box-shadow: 0 2px 10px rgba(0, 0, 0, 0.1);
}

.toggle-button {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  background-color: #3498db;
  border: none;
  border-radius: 5px;
  color: white;
  cursor: pointer;
  font-size: 16px;
  margin-bottom: 1rem;
  padding: 0.5rem 1rem;
  transition: background-color 0.3s ease;
}

.toggle-button:hover {
  background-color: #2980b9;
}

.burger-icon {
  width: 30px;
  height: 4px;
  background-color: white;
  margin: 5px auto;
}

.about-content {
  display: flex;
  align-items: center;
  margin-top: 1rem;
  padding: 1rem;
}

.profile-image {
  width: 150px;
  border-radius: 75px;
  margin-right: 20px;
  box-shadow: 0 2px 10px rgba(0, 0, 0, 0.2);
}

.social-container {
  display: flex;
  justify-content: center;
  margin-top: 1.5rem;
}

.social-logo {
  width: 80px; /* Increased size */
  height: 80px;
  cursor: pointer;
  transition: transform 0.3s ease;
}

.social-logo:hover {
  transform: scale(1.1);
}

.about-text {
  flex: 1;
  text-align: center; /* Center-aligns the content */
}

.about-text p {
  margin-bottom: 1rem;
  line-height: 1.6;
  font-size: 1rem;
  color: #030303;
}
</style>
