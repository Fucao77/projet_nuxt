<template>
  <div class="product-detail">
    <div class="container">
      <div class="breadcrumb">
        <NuxtLink to="/">Accueil</NuxtLink> /
        <NuxtLink :to="`/${product.category.toLowerCase()}`">{{ product.category }}</NuxtLink> /
        <span>{{ product.name }}</span>
      </div>
      
      <div class="product-content">
        <div class="product-gallery">
          <div class="main-image">
            <img :src="product.image" :alt="product.name" />
          </div>
          <div class="thumbnails">
            <div v-for="i in 4" :key="i" class="thumbnail" :class="{ active: i === 1 }">
              <img :src="product.image" :alt="`${product.name} view ${i}`" />
            </div>
          </div>
        </div>
        
        <div class="product-info">
          <h1 class="product-name">{{ product.name }}</h1>
          <div class="product-category">{{ product.category }}</div>
          <div class="product-price">{{ formatPrice(product.price) }} €</div>
          
          <div class="product-description">
            <p>
              Les chaussures Nike {{ product.name }} offrent un amorti exceptionnel et un style emblématique. 
              Conçues pour le confort quotidien, elles allient performance et design élégant pour 
              vous accompagner toute la journée.
            </p>
          </div>
          
          <div class="product-options">
            <div class="option-label">Taille:</div>
            <div class="size-selector">
              <button 
                v-for="size in sizes" 
                :key="size" 
                :class="{ active: selectedSize === size }"
                @click="selectedSize = size"
              >
                {{ size }}
              </button>
            </div>
            
            <div class="option-label">Couleur:</div>
            <div class="color-selector">
              <button 
                v-for="(color, index) in colors" 
                :key="index" 
                :class="{ active: selectedColor === index }"
                :style="{ backgroundColor: color }"
                @click="selectedColor = index"
              ></button>
            </div>
          </div>
          
          <div class="product-actions">
            <div class="quantity-selector">
              <button @click="decrementQuantity" :disabled="quantity <= 1">-</button>
              <input type="number" v-model="quantity" min="1" />
              <button @click="incrementQuantity">+</button>
            </div>
            
            <button class="add-to-cart-btn" @click="addToCart">
              Ajouter au panier
            </button>
            
            <button class="favorite-btn" @click="toggleFavorite">
              <span class="material-icons">{{ isFavorite ? 'favorite' : 'favorite_border' }}</span>
            </button>
          </div>
          
          <div class="product-meta">
            <div>
              <span class="material-icons">inventory_2</span>
              <span>En stock</span>
            </div>
            <div>
              <span class="material-icons">local_shipping</span>
              <span>Livraison gratuite à partir de 100€</span>
            </div>
            <div>
              <span class="material-icons">replay</span>
              <span>Retours gratuits sous 30 jours</span>
            </div>
          </div>
        </div>
      </div>
      
      <div class="related-products">
        <h2>Vous aimerez aussi</h2>
        <div class="products-grid">
          <ProductCard 
            v-for="i in 4" 
            :key="i" 
            :product="{ 
              id: i + 10, 
              name: 'Nike Air Zoom ' + i, 
              price: 129.99, 
              image: `https://static.nike.com/a/images/c_limit,w_592,f_auto/t_product_v1/1eeaee4a-e5dd-4a77-891e-31086896${i}b82/chaussure-air-force-1-07-pour-T4sC8z.png`,
              category: 'Chaussures'
            }" 
          />
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
definePageMeta({
  layout: 'default'
});

const route = useRoute();
const productId = route.params.id;

// Dans un cas réel, ces données viendraient d'une API
const product = reactive({
  id: productId,
  name: 'Nike Air Max 270',
  price: 159.99,
  category: 'Chaussures',
  image: 'https://static.nike.com/a/images/c_limit,w_592,f_auto/t_product_v1/dd35d974-5780-4f28-93e6-3199025e4480/chaussure-air-max-270-pour-pLRB73.png',
});

const sizes = ['38', '39', '40', '41', '42', '43', '44', '45'];
const colors = ['#000000', '#FFFFFF', '#FF0000', '#0000FF'];

const selectedSize = ref('42');
const selectedColor = ref(0);
const quantity = ref(1);
const isFavorite = ref(false);

const incrementQuantity = () => {
  quantity.value++;
};

const decrementQuantity = () => {
  if (quantity.value > 1) {
    quantity.value--;
  }
};

const toggleFavorite = () => {
  isFavorite.value = !isFavorite.value;
};

const addToCart = () => {
  // Logique pour ajouter au panier (à implémenter plus tard)
  console.log('Produit ajouté au panier:', {
    ...product,
    size: selectedSize.value,
    color: colors[selectedColor.value],
    quantity: quantity.value
  });
};

const formatPrice = (price) => {
  return price.toFixed(2).replace('.', ',');
};
</script>

<style scoped>
.product-detail {
  padding-top: 120px;
  padding-bottom: 80px;
}

.breadcrumb {
  margin-bottom: 30px;
  font-size: 0.9rem;
}

.breadcrumb a {
  color: var(--text-color);
  text-decoration: none;
}

.breadcrumb a:hover {
  color: var(--accent-color);
}

.product-content {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 50px;
  margin-bottom: 80px;
}

.product-gallery {
  display: flex;
  flex-direction: column;
  gap: 20px;
}

.main-image {
  background-color: #f8f8f8;
  border-radius: 10px;
  overflow: hidden;
  display: flex;
  align-items: center;
  justify-content: center;
  height: 500px;
}

.main-image img {
  max-width: 100%;
  max-height: 100%;
  object-fit: contain;
}

.thumbnails {
  display: flex;
  gap: 10px;
}

.thumbnail {
  width: 80px;
  height: 80px;
  border-radius: 8px;
  overflow: hidden;
  background-color: #f8f8f8;
  cursor: pointer;
  border: 2px solid transparent;
}

.thumbnail.active {
  border-color: var(--accent-color);
}

.thumbnail img {
  width: 100%;
  height: 100%;
  object-fit: contain;
}

.product-name {
  font-size: 2.5rem;
  font-weight: 700;
  margin-bottom: 10px;
}

.product-category {
  color: #777;
  margin-bottom: 15px;
}

.product-price {
  font-size: 1.8rem;
  font-weight: 700;
  margin-bottom: 20px;
  color: var(--accent-color);
}

.product-description {
  margin-bottom: 30px;
  line-height: 1.6;
}

.product-options {
  margin-bottom: 30px;
}

.option-label {
  font-weight: 600;
  margin-bottom: 10px;
}

.size-selector, .color-selector {
  display: flex;
  flex-wrap: wrap;
  gap: 10px;
  margin-bottom: 20px;
}

.size-selector button {
  width: 50px;
  height: 50px;
  border: 1px solid #ddd;
  background-color: white;
  border-radius: 8px;
  display: flex;
  align-items: center;
  justify-content: center;
  cursor: pointer;
  font-weight: 600;
  transition: all 0.3s ease;
}

.size-selector button.active, .size-selector button:hover {
  border-color: var(--secondary-color);
  background-color: var(--secondary-color);
  color: white;
}

.color-selector button {
  width: 30px;
  height: 30px;
  border-radius: 50%;
  border: 2px solid transparent;
  cursor: pointer;
  position: relative;
}

.color-selector button.active {
  border-color: var(--secondary-color);
}

.color-selector button.active::after {
  content: '';
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  width: 40px;
  height: 40px;
  border-radius: 50%;
  border: 1px solid var(--secondary-color);
}

.product-actions {
  display: flex;
  gap: 15px;
  margin-bottom: 30px;
}

.quantity-selector {
  display: flex;
  align-items: center;
  border: 1px solid #ddd;
  border-radius: 30px;
  overflow: hidden;
}

.quantity-selector button {
  width: 40px;
  height: 40px;
  background-color: white;
  border: none;
  cursor: pointer;
  font-size: 1.2rem;
}

.quantity-selector input {
  width: 60px;
  height: 40px;
  text-align: center;
  border: none;
  border-left: 1px solid #ddd;
  border-right: 1px solid #ddd;
}

.add-to-cart-btn {
  flex: 1;
  padding: 0 30px;
  height: 40px;
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

.favorite-btn {
  width: 40px;
  height: 40px;
  border-radius: 50%;
  border: 1px solid #ddd;
  background-color: white;
  display: flex;
  align-items: center;
  justify-content: center;
  cursor: pointer;
}

.favorite-btn .material-icons {
  color: var(--accent-color);
}

.product-meta {
  margin-top: 30px;
  padding-top: 20px;
  border-top: 1px solid #ddd;
}

.product-meta div {
  display: flex;
  align-items: center;
  gap: 10px;
  margin-bottom: 10px;
}

.related-products h2 {
  font-size: 1.8rem;
  margin-bottom: 30px;
}

.products-grid {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(250px, 1fr));
  gap: 30px;
}

@media (max-width: 768px) {
  .product-content {
    grid-template-columns: 1fr;
  }
  
  .main-image {
    height: 350px;
  }
  
  .product-name {
    font-size: 2rem;
  }
}
</style> 