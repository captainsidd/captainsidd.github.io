<script setup lang="ts">
import { ref } from 'vue'

import LinkedIn from './icons/linkedin.svg';
import GitHub from './icons/github.svg';
import Blog from './icons/blog.svg';
import Instagram from './icons/instagram.svg';
import Harmonic from './icons/harmonicdecisions.svg';
import Profile from '../assets/profile.jpg';

const name = 'Hi, I\'m Sid.';
const bio = 'I like understanding why we make decisions and building systems to help us make better ones.';
const hoverText = ref('');

const links = [
  { url: 'https://asidnote.ghost.io', image: Blog, text: 'Read my assorted writings' },
  { url: 'https://linkedin.com/in/cptsidd', image: LinkedIn, text: 'Connect with me on LinkedIn' },
  { url: 'https://harmonicdecisions.com', image: Harmonic, text: 'Let me help you make decisions' },
  { url: 'https://instagram.com/sid.nutul', image: Instagram, text: 'Add me on Instagram I guess' },
  { url: 'https://github.com/captainsidd', image: GitHub, text: 'Find my software engineering work on GitHub' },
];

const updateHoverText = (newText) => {
  hoverText.value = newText;
}
</script>

<template>
  <div class="profile-page">
    <div class="profile-container">
      <img class="profile-picture" :src="Profile" alt="If you can read this my face isn't showing up" />
      <div class="greeting-container">
        <h1 class="greeting">{{ name }}</h1>
      </div>
      <div class="bio-container">
        <p class="bio">{{ bio }}</p>
      </div>

      <div class="links-container">
        <div
          v-for="(link, index) in links"
          :key="index"
          class="link"
          @mouseover="updateHoverText(link.text)"
          @mouseleave="updateHoverText('')"
        >
          <a :href="link.url" target="_blank">
            <img :src="link.image" :alt="link.text" />
          </a>
        </div>
      </div>
      <div class="hover-container">
        <p class="hover-text" v-if="hoverText">{{ hoverText }}</p>
      </div>
    </div>
  </div>
</template>


<style scoped>
.profile-page {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: space-between;
  height: 95vh;
  padding-top: 15vh;
  padding-bottom: 15vh;
  box-sizing: border-box;
}

.profile-container {
  text-align: center;
  position: relative;
}

.profile-picture {
  width: 150px;
  height: 150px;
  border-radius: 50%;
  object-fit: cover;
  margin-bottom: 20px;
}

.greeting-container {
  display: flex;
  flex-direction: row;
  align-items: center;
  justify-content: center;
}

.greeting {
  text-align: center;
  font-size: 96px;
  margin-bottom: 10px;
}

.bio {
  font-size: 36px;
  margin-bottom: 10px;
}

.hover-text {
  font-size: 16px;
}

.links-container {
  display: flex;
  flex-direction: row;
  align-items: center;
  justify-content: center;
  gap: 2%;
}

.link {
  padding: 10px;
}

.link img {
  max-width: 50px;
  height: 50px;
  filter: grayscale(100%);
  transition: filter 0.3s ease;
}

.link img:hover {
  filter: none;
}

@media screen and (max-width: 600px) {
  .greeting {
    font-size: 60px;
  }

  .bio {
    font-size: 18px;
  }

  .hover-text {
    font-size: 12px;
  }

  .links-container {
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    gap: 2%;
  }
}
</style>