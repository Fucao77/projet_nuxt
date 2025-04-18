<template>
  <header class="header">
    <div class="container">
      <nav class="navbar">
        <div class="logo">
          <NuxtLink to="/">
            <img src="/images/nike-logo.svg" alt="Nike Logo" height="40" />
          </NuxtLink>
        </div>
        <div class="nav-links" :class="{ 'active': isMenuOpen }">
          <ul>
            <li><NuxtLink to="/">Accueil</NuxtLink></li>
            <li><NuxtLink to="/hommes">Hommes</NuxtLink></li>
            <li><NuxtLink to="/femmes">Femmes</NuxtLink></li>
            <li><NuxtLink to="/enfants">Enfants</NuxtLink></li>
            <li><NuxtLink to="/collections">Collections</NuxtLink></li>
          </ul>
        </div>
        <div class="nav-actions">
          <button class="search-btn">
            <span class="material-icons">search</span>
          </button>
          <button class="cart-btn">
            <span class="material-icons">shopping_bag</span>
          </button>
          <button class="mobile-menu-btn" @click="toggleMenu">
            <span class="material-icons">{{ isMenuOpen ? 'close' : 'menu' }}</span>
          </button>
        </div>
      </nav>
    </div>
  </header>
</template>

<script setup>
const isMenuOpen = ref(false);

const toggleMenu = () => {
  isMenuOpen.value = !isMenuOpen.value;
};
</script>

<style scoped>
.header {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  background-color: white;
  box-shadow: 0 2px 10px rgba(0, 0, 0, 0.1);
  z-index: 1000;
}

.navbar {
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 15px 0;
}

.logo {
  flex: 0 0 auto;
}

.nav-links ul {
  display: flex;
  list-style: none;
  gap: 30px;
}

.nav-links a {
  text-decoration: none;
  color: var(--text-color);
  font-weight: 500;
  transition: color 0.3s ease;
}

.nav-links a:hover {
  color: var(--accent-color);
}

.nav-actions {
  display: flex;
  gap: 15px;
}

.nav-actions button {
  background: none;
  border: none;
  cursor: pointer;
  font-size: 24px;
}

.mobile-menu-btn {
  display: none;
}

@media (max-width: 768px) {
  .nav-links {
    position: fixed;
    top: 70px;
    left: 0;
    right: 0;
    background-color: white;
    padding: 20px;
    box-shadow: 0 5px 10px rgba(0, 0, 0, 0.1);
    transform: translateY(-100%);
    transition: transform 0.3s ease;
    z-index: 999;
  }

  .nav-links.active {
    transform: translateY(0);
  }

  .nav-links ul {
    flex-direction: column;
    gap: 15px;
  }

  .mobile-menu-btn {
    display: block;
  }
}
</style> 