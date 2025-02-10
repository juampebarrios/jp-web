<template>
  <nav class="navbar">
    <div class="container">
      <NuxtLink to="/" class="logo">jp-web</NuxtLink>

      <ul class="nav-links" :class="{ 'open': isOpen }">
        <li v-for="link in navLinks" :key="link.to">
          <NuxtLink :to="link.to">{{ link.label }}</NuxtLink>
        </li>
      </ul>

      <button class="menu-toggle" @click="isOpen = !isOpen">
        <span v-if="!isOpen">&#9776;</span>
        <span v-else>&times;</span>
      </button>
    </div>
  </nav>
</template>

<script setup>
import { ref } from "vue";

const isOpen = ref(false);

const navLinks = [
  { to: "/", label: "Home" },
  { to: "/about", label: "About" },
  { to: "/contact", label: "Contact" },
];
</script>

<style scoped>
.navbar {
  background: #222;
  color: white;
  padding: 10px 20px;
}

.container {
  display: flex;
  justify-content: space-between;
  align-items: center;
  max-width: 1200px;
  margin: 0 auto;
}

.logo {
  font-size: 1.5rem;
  font-weight: bold;
  color: white;
  text-decoration: none;
}

.nav-links {
  list-style: none;
  display: flex;
  gap: 20px;
  margin: 0;
  padding: 0;
}

.nav-links li a {
  color: white;
  text-decoration: none;
  padding: 5px 10px;
}

.nav-links li a:hover {
  color: #ddd;
}

.menu-toggle {
  background: none;
  border: none;
  color: white;
  font-size: 1.5rem;
  cursor: pointer;
  display: none;
}

@media (max-width: 768px) {
  .menu-toggle {
    display: block;
  }

  .nav-links {
    position: absolute;
    top: 60px;
    right: 0;
    background: #222;
    flex-direction: column;
    width: 200px;
    text-align: center;
    display: none;
    padding: 10px 0;
  }

  .nav-links.open {
    display: flex;
  }

  .nav-links li {
    padding: 10px 0;
  }
}
</style>
