<template>
  <div class="showcases">
    <Header /> <!-- Header component for the page -->

    <main class="showcases-content">
      <h2>My Showcases</h2> <!-- Main heading -->

      <div class="showcases-grid">
        <div class="showcase-card" v-for="showcase in showcases" :key="showcase.id">
          <a :href="showcase.image" target="_blank" rel="noopener noreferrer"> <!-- Link to project image -->
            <img :src="showcase.image" alt="Showcase Image" class="showcase-image" /> <!-- Displaying showcase image -->
          </a>
          <div class="showcase-details">
            <h3>{{ showcase.name }}</h3> <!-- Showcase name -->
            <p class="description">{{ showcase.description }}</p> <!-- Project description -->
            <p v-if="showcase.date" class="date">Date: {{ showcase.date }}</p> <!-- Optional date -->
          </div>
        </div>
      </div>
    </main>

    <Footer /> <!-- Footer component for the page -->
  </div>
</template>

<script>
import Header from './Header.vue'; // Import Header component
import Footer from './Footer.vue'; // Import Footer component

// Importing showcase images
import proj1 from '@/assets/proj1.jpg';
import cert1 from '@/assets/cert1.jpg';
import cert2 from '@/assets/cert2.jpg';
import cert3 from '@/assets/cert3.jpg';
import cert4 from '@/assets/cert4.jpg';

export default {
  name: 'Showcases', // Component name
  components: {
    Header,
    Footer
  },
  data() {
    return {
      showcases: [
        {
          id: 1,
          name: 'CalcGrab',
          description: 'A system that allows you to compute using multiple types of calculators.',
          image: proj1,
        },
        {
          id: 2,
          name: 'CCNAv7: Enterprise Networking, Security, and Automation.',
          description: 'CISCO certification showcasing expertise in enterprise networking.',
          date: '2024-05-10',
          image: cert1,
        },
        {
          id: 3,
          name: 'CCNAv7: Introduction to Networks',
          description: 'CISCO certification on foundational networking concepts.',
          date: '2024-07-22',
          image: cert2,
        },
        {
          id: 4,
          name: 'CCNAv7: Switching, Routing, and Wireless Essentials',
          description: 'CISCO certification covering intermediate networking skills.',
          date: '2023-01-16',
          image: cert3,
        },
        {
          id: 5,
          name: 'Cybersecurity Essentials',
          description: 'CISCO certification focusing on core cybersecurity principles.',
          date: '2023-05-17',
          image: cert4,
        },
      ],
    };
  },
  mounted() {
    // Optional: Sort showcases by date if applicable
    this.showcases.sort((a, b) => new Date(b.date || '1970-01-01') - new Date(a.date || '1970-01-01'));
  }
};
</script>

<style scoped>
.showcases {
  display: flex;
  flex-direction: column;
  height: 100vh;
  background-color: #f9f9f9;
}

.showcases-content {
  flex: 1;
  max-width: 1000px;
  margin: 0 auto;
  padding: 20px;
  overflow-y: scroll;
  scrollbar-width: none;
}

.showcases-content::-webkit-scrollbar {
  display: none;
}

h2 {
  font-size: 2rem;
  font-weight: 600;
  margin-bottom: 20px;
  text-align: center;
  color: #333;
}

.showcases-grid {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(250px, 1fr));
  gap: 20px;
}

.showcase-card {
  background-color: #b5bfec;
  border-radius: 10px;
  box-shadow: 0 4px 10px rgba(0, 0, 0, 0.1);
  overflow: hidden;
  transition: transform 0.3s ease, box-shadow 0.3s ease;
  cursor: pointer;
}

.showcase-card:hover {
  transform: translateY(-5px);
  box-shadow: 0 8px 20px rgba(0, 0, 0, 0.2);
}

.showcase-image {
  width: 100%;
  height: auto;
  transition: transform 0.3s ease;
}

.showcase-card:hover .showcase-image {
  transform: scale(1.05);
}

.showcase-details {
  padding: 15px;
  color: #555;
}

.showcase-details h3 {
  font-size: 1.5rem;
  margin: 0 0 5px;
  color: #2c3e50;
}

.showcase-details .description,
.showcase-details .date {
  color: #777;
  margin: 0;
  font-size: 0.9rem;
}
</style>
