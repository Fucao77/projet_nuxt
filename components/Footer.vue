<template>
  <footer class="footer">
    <div class="container">
      <div class="footer-content">
        <div class="footer-section">
          <h4>PRODUITS</h4>
          <ul>
            <li><NuxtLink to="/chaussures">Chaussures</NuxtLink></li>
            <li><NuxtLink to="/vetements">Vêtements</NuxtLink></li>
            <li><NuxtLink to="/accessoires">Accessoires</NuxtLink></li>
            <li><NuxtLink to="/collections">Collections</NuxtLink></li>
          </ul>
        </div>
        <div class="footer-section">
          <h4>NIKE</h4>
          <ul>
            <li><NuxtLink to="/a-propos">À propos</NuxtLink></li>
            <li><NuxtLink to="/actualites">Actualités</NuxtLink></li>
            <li><NuxtLink to="/carrieres">Carrières</NuxtLink></li>
            <li><NuxtLink to="/investisseurs">Investisseurs</NuxtLink></li>
          </ul>
        </div>
        <div class="footer-section">
          <h4>AIDE</h4>
          <ul>
            <li><NuxtLink to="/commande">Statut de la commande</NuxtLink></li>
            <li><NuxtLink to="/livraison">Expédition et livraison</NuxtLink></li>
            <li><NuxtLink to="/retours">Retours</NuxtLink></li>
            <li><NuxtLink to="/contact">Nous contacter</NuxtLink></li>
          </ul>
        </div>
        <div class="footer-section social">
          <h4>SUIVEZ-NOUS</h4>
          <div class="social-links">
            <a href="#" aria-label="Facebook"><span class="material-icons">facebook</span></a>
            <a href="#" aria-label="Twitter"><span class="material-icons">twitter</span></a>
            <a href="#" aria-label="Instagram"><span class="material-icons">instagram</span></a>
            <a href="#" aria-label="YouTube"><span class="material-icons">youtube</span></a>
          </div>
        </div>
      </div>
      <div class="footer-bottom">
        <div class="copyright">
          <p>&copy; {{ new Date().getFullYear() }} Nike, Inc. Tous droits réservés.</p>
        </div>
        <div class="legal-links">
          <NuxtLink to="/conditions">Conditions d'utilisation</NuxtLink>
          <NuxtLink to="/confidentialite">Politique de confidentialité</NuxtLink>
          <NuxtLink to="/cookies">Gestion des cookies</NuxtLink>
        </div>
      </div>
    </div>
  </footer>
</template>

<script setup>
// Pas de logique supplémentaire nécessaire
</script>

<style scoped>
.footer {
  background-color: var(--secondary-color);
  color: white;
  padding: 60px 0 30px;
}

.footer-content {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
  gap: 30px;
  margin-bottom: 40px;
}

.footer-section h4 {
  font-size: 16px;
  margin-bottom: 20px;
  font-weight: 600;
}

.footer-section ul {
  list-style: none;
}

.footer-section li {
  margin-bottom: 10px;
}

.footer-section a {
  color: #ccc;
  text-decoration: none;
  transition: color 0.3s ease;
}

.footer-section a:hover {
  color: white;
}

.social-links {
  display: flex;
  gap: 15px;
}

.social-links a {
  display: flex;
  align-items: center;
  justify-content: center;
  width: 40px;
  height: 40px;
  border-radius: 50%;
  background-color: rgba(255, 255, 255, 0.1);
  transition: background-color 0.3s ease;
}

.social-links a:hover {
  background-color: rgba(255, 255, 255, 0.2);
}

.footer-bottom {
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding-top: 30px;
  border-top: 1px solid rgba(255, 255, 255, 0.1);
}

.copyright {
  color: #ccc;
  font-size: 14px;
}

.legal-links {
  display: flex;
  gap: 20px;
}

.legal-links a {
  color: #ccc;
  text-decoration: none;
  font-size: 14px;
  transition: color 0.3s ease;
}

.legal-links a:hover {
  color: white;
}

@media (max-width: 768px) {
  .footer-bottom {
    flex-direction: column;
    gap: 20px;
    text-align: center;
  }

  .legal-links {
    flex-direction: column;
    gap: 10px;
  }
}
</style> 