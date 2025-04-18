<template>
  <div>
    <!-- Section Héro -->
    <section class="hero">
      <div class="container hero-container">
        <div class="hero-content">
          <h1>JUST DO IT</h1>
          <p>Découvrez les dernières innovations Nike pour vous aider à atteindre vos objectifs sportifs.</p>
          <div class="hero-buttons">
            <NuxtLink to="/collections/nouveautes" class="btn btn-primary">Découvrir</NuxtLink>
            <NuxtLink to="/collections" class="btn btn-outline">Collections</NuxtLink>
          </div>
        </div>
        <div class="hero-image">
          <img src="https://static.nike.com/a/images/t_PDP_864_v1/f_auto,b_rgb:f5f5f5/17c9e2f4-57ec-40f1-a54d-cf1319b1626c/chaussure-air-max-plus-pour-3sKmLw.png" alt="Nike Shoes" />
        </div>
      </div>
    </section>

    <!-- Bannière de promotion -->
    <section class="promo-banner">
      <div class="container">
        <p>Livraison gratuite pour les membres Nike. <NuxtLink to="/membre">Rejoignez-nous</NuxtLink></p>
      </div>
    </section>

    <!-- Section Nouveautés -->
    <section class="section new-arrivals">
      <div class="container">
        <div class="section-header">
          <h2>Nouveautés</h2>
          <NuxtLink to="/collections/nouveautes" class="view-all">Voir tout</NuxtLink>
        </div>
        <div class="products-grid">
          <ProductCard 
            v-for="i in 4" 
            :key="i" 
            :product="{ 
              id: i, 
              name: 'Nike Air Max ' + i, 
              price: 159.99, 
              image: 'https://static.nike.com/a/images/c_limit,w_592,f_auto/t_product_v1/36a7d256-5incorrectnumber-ca68-4c8a-8cae-2a0f8a9f561e/chaussure-air-max-plus-pour-3sKmLw.png'.replace('incorrectnumber', i),
              category: 'Chaussures'
            }" 
          />
        </div>
      </div>
    </section>

    <!-- Section Collections -->
    <section class="section collections">
      <div class="container">
        <div class="section-header">
          <h2>Collections</h2>
        </div>
        <div class="collections-grid">
          <div class="collection-card">
            <div class="collection-image">
              <img src="https://static.nike.com/a/images/f_auto/dpr_1.0,cs_srgb/w_906,c_limit/d9c6a623-8862-4cc0-97cc-95a1cf5c9e5b/homme.jpg" alt="Collection Hommes" />
            </div>
            <div class="collection-overlay">
              <h3>Hommes</h3>
              <NuxtLink to="/hommes" class="btn btn-outline">Découvrir</NuxtLink>
            </div>
          </div>
          <div class="collection-card">
            <div class="collection-image">
              <img src="https://static.nike.com/a/images/f_auto/dpr_1.0,cs_srgb/w_906,c_limit/d5b7acfb-a70b-4a1c-8a03-2abe40be0223/femme.jpg" alt="Collection Femmes" />
            </div>
            <div class="collection-overlay">
              <h3>Femmes</h3>
              <NuxtLink to="/femmes" class="btn btn-outline">Découvrir</NuxtLink>
            </div>
          </div>
          <div class="collection-card">
            <div class="collection-image">
              <img src="https://static.nike.com/a/images/f_auto/dpr_1.0,cs_srgb/w_906,c_limit/fd18b1e2-389c-4ca6-b178-ed4c737ccb9e/enfant.jpg" alt="Collection Enfants" />
            </div>
            <div class="collection-overlay">
              <h3>Enfants</h3>
              <NuxtLink to="/enfants" class="btn btn-outline">Découvrir</NuxtLink>
            </div>
          </div>
        </div>
      </div>
    </section>

    <!-- Section À la une -->
    <section class="section featured">
      <div class="container">
        <div class="featured-content">
          <h2>NIKE AIR FORCE 1</h2>
          <p>Une icône revisitée pour une nouvelle génération.</p>
          <NuxtLink to="/collections/air-force-1" class="btn btn-primary">Acheter</NuxtLink>
        </div>
        <div class="featured-image">
          <img src="https://static.nike.com/a/images/t_PDP_1280_v1/f_auto,q_auto:eco/1a853229-0449-4175-9931-78c8fef4c109/chaussure-air-force-1-07-pour-HfCJJk.png" alt="Nike Air Force 1" />
        </div>
      </div>
    </section>
  </div>
</template>

<script setup>
definePageMeta({
  layout: 'default'
});
</script>

<style scoped>
.hero {
  padding: 120px 0 80px;
  background-color: #f5f5f5;
  position: relative;
  overflow: hidden;
  margin-top: 70px;
}

.hero-container {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 40px;
  align-items: center;
}

.hero-content {
  z-index: 2;
}

.hero-content h1 {
  font-size: 4rem;
  font-weight: 900;
  margin-bottom: 20px;
  line-height: 1.1;
}

.hero-content p {
  font-size: 1.25rem;
  margin-bottom: 30px;
  max-width: 500px;
}

.hero-buttons {
  display: flex;
  gap: 15px;
}

.hero-image {
  position: relative;
  z-index: 1;
  display: flex;
  justify-content: center;
}

.hero-image img {
  max-width: 100%;
  transform: rotate(-15deg);
  filter: drop-shadow(0 20px 30px rgba(0, 0, 0, 0.2));
}

.promo-banner {
  background-color: var(--secondary-color);
  color: white;
  padding: 15px 0;
  text-align: center;
}

.promo-banner a {
  color: white;
  font-weight: 600;
  text-decoration: underline;
}

.section-header {
  display: flex;
  justify-content: space-between;
  align-items: center;
  margin-bottom: 40px;
}

.section-header h2 {
  font-size: 2rem;
  font-weight: 700;
}

.view-all {
  color: var(--accent-color);
  text-decoration: none;
  font-weight: 600;
}

.products-grid {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(250px, 1fr));
  gap: 30px;
}

.collections-grid {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 20px;
}

.collection-card {
  position: relative;
  height: 400px;
  overflow: hidden;
  border-radius: 8px;
}

.collection-image {
  height: 100%;
  width: 100%;
}

.collection-image img {
  width: 100%;
  height: 100%;
  object-fit: cover;
  transition: transform 0.5s ease;
}

.collection-card:hover .collection-image img {
  transform: scale(1.05);
}

.collection-overlay {
  position: absolute;
  bottom: 0;
  left: 0;
  right: 0;
  padding: 30px;
  background: linear-gradient(to top, rgba(0, 0, 0, 0.7), transparent);
  color: white;
  transition: background 0.3s ease;
}

.collection-overlay h3 {
  font-size: 1.75rem;
  margin-bottom: 15px;
}

.featured {
  background-color: #f8f8f8;
  overflow: hidden;
}

.featured .container {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 40px;
  align-items: center;
}

.featured-content h2 {
  font-size: 3rem;
  font-weight: 900;
  margin-bottom: 20px;
}

.featured-content p {
  font-size: 1.25rem;
  margin-bottom: 30px;
}

.featured-image img {
  max-width: 100%;
  transform: rotate(-10deg);
  filter: drop-shadow(0 20px 30px rgba(0, 0, 0, 0.15));
}

@media (max-width: 768px) {
  .hero-container,
  .featured .container {
    grid-template-columns: 1fr;
  }

  .hero-content h1 {
    font-size: 3rem;
  }

  .collections-grid {
    grid-template-columns: 1fr;
  }

  .collection-card {
    height: 300px;
  }
}
</style> 