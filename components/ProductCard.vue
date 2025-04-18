<template>
  <div class="product-card">
    <div class="product-image">
      <NuxtLink :to="`/produit/${product.id}`">
        <img :src="product.image" :alt="product.name" />
      </NuxtLink>
      <button class="favorite-btn" @click="toggleFavorite">
        <span class="material-icons">{{ isFavorite ? 'favorite' : 'favorite_border' }}</span>
      </button>
    </div>
    <div class="product-info">
      <span class="product-category">{{ product.category }}</span>
      <h3 class="product-name">
        <NuxtLink :to="`/produit/${product.id}`">{{ product.name }}</NuxtLink>
      </h3>
      <div class="product-price">{{ formatPrice(product.price) }} €</div>
      <button class="add-to-cart-btn" @click="addToCart">Ajouter au panier</button>
    </div>
  </div>
</template>

<script setup>
const props = defineProps({
  product: {
    type: Object,
    required: true
  }
});

const isFavorite = ref(false);

const toggleFavorite = () => {
  isFavorite.value = !isFavorite.value;
};

const addToCart = () => {
  // Logique pour ajouter au panier (à implémenter plus tard)
  console.log('Produit ajouté au panier:', props.product.name);
};

const formatPrice = (price) => {
  return price.toFixed(2).replace('.', ',');
};
</script>

<style scoped>
.product-card {
  background-color: white;
  border-radius: 8px;
  overflow: hidden;
  box-shadow: 0 2px 10px rgba(0, 0, 0, 0.05);
  transition: transform 0.3s ease, box-shadow 0.3s ease;
}

.product-card:hover {
  transform: translateY(-5px);
  box-shadow: 0 5px 15px rgba(0, 0, 0, 0.1);
}

.product-image {
  position: relative;
  height: 250px;
  background-color: #f8f8f8;
  display: flex;
  align-items: center;
  justify-content: center;
  overflow: hidden;
}

.product-image img {
  max-width: 100%;
  max-height: 100%;
  object-fit: contain;
  transition: transform 0.5s ease;
}

.product-card:hover .product-image img {
  transform: scale(1.05);
}

.favorite-btn {
  position: absolute;
  top: 10px;
  right: 10px;
  background: white;
  border: none;
  border-radius: 50%;
  width: 36px;
  height: 36px;
  display: flex;
  align-items: center;
  justify-content: center;
  cursor: pointer;
  box-shadow: 0 2px 5px rgba(0, 0, 0, 0.1);
  z-index: 1;
  transition: background-color 0.3s ease;
}

.favorite-btn:hover {
  background-color: #f5f5f5;
}

.favorite-btn .material-icons {
  color: var(--accent-color);
  font-size: 20px;
}

.product-info {
  padding: 20px;
}

.product-category {
  display: block;
  font-size: 0.85rem;
  color: #777;
  margin-bottom: 5px;
}

.product-name {
  font-weight: 600;
  margin-bottom: 10px;
  font-size: 1.1rem;
}

.product-name a {
  color: var(--text-color);
  text-decoration: none;
  transition: color 0.3s ease;
}

.product-name a:hover {
  color: var(--accent-color);
}

.product-price {
  font-weight: 700;
  font-size: 1.2rem;
  margin-bottom: 15px;
}

.add-to-cart-btn {
  width: 100%;
  padding: 10px 0;
  background-color: var(--secondary-color);
  color: white;
  border: none;
  border-radius: 30px;
  font-weight: 600;
  cursor: pointer;
  transition: background-color 0.3s ease;
}

.add-to-cart-btn:hover {
  background-color: #000;
}
</style> 