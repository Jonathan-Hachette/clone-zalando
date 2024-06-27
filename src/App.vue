<script setup>
import Header from './components/Header.vue'
import Footer from './components/Footer.vue'

// Import du fichier JSON contenant les informations relatives au produit
import productInfos from './assets/data.json'
</script>

<template>
  <div>
    <Header />
    <main class="container">
      <!-- Wrapper -->

      <!-- Première colonne photos du produit -->
      <div>
        <img src="" alt="" />
      </div>
      <!-- Deuxième colonne affichage des informations du produit -->
      <div class="colonne-droite">
        <h2>{{ productInfos.brand }}</h2>
        <h1>{{ productInfos.name }}</h1>
        <p>{{ productInfos.price }} € <span>TVA incluse</span></p>
        <div class="rate">
          <font-awesome-icon :icon="['fas', 'star']" size="lg" />
          <font-awesome-icon :icon="['fas', 'star']" size="lg" />
          <font-awesome-icon :icon="['fas', 'star']" size="lg" />
          <font-awesome-icon :icon="['fas', 'star']" size="lg" />
          <font-awesome-icon :icon="['fas', 'star-half-alt']" size="lg" />
          <span>{{ productInfos.rate }}</span>
        </div>
        <p><span>Couleur :</span> Bleu</p>
        <div>
          <img src="" alt="t-shirt bleu" />
          <img src="" alt="t-shirt jaune" />
          <img src="" alt="t-shirt rose" />
        </div>
        <p class="advise">
          Nous vous recommandons de choisir une taille au-dessus de celle habituelle.
        </p>
        <div class="sizes">
          <div>XS</div>
          <div>S</div>
          <div>M</div>
          <div>L</div>
          <div>XL</div>
        </div>
        <div class="cart-bloc">
          <button>Ajouter au panier</button>
          <div>
            <font-awesome-icon :icon="['far', 'heart']" />
          </div>
        </div>
      </div>
    </main>

    <Footer />
  </div>
</template>

<style scoped>
.container {
  display: flex;
  height: calc(
    100vh - var(--header-top-height) - var(--header-bottom-height) - var(--footer-height)
  );
}
.container > div {
  width: 50%;
  border: 1px solid green;
}

.container > div:last-child {
  display: flex;
  flex-direction: column;
  padding: 25px 0 25px 100px;
}

h1 + p {
  font-size: 22px;
  margin-bottom: 25px;
}

h1 + p span {
  color: #66676e;
  font-size: 14px;
  font-weight: lighter;
}

.rate {
  margin-bottom: 40px;
}

.rate svg {
  margin-right: 4px;
}

.advise {
  background-color: var(--light-grey);
  padding: 20px;
  font-size: 14px;
  line-height: 20px;
  font-weight: lighter;
  margin-bottom: 10px;
}

.sizes {
  display: flex;
  justify-content: center;
  align-items: center;
  gap: 10px;
}

.sizes div {
  display: flex;
  align-items: center;
  justify-content: center;
  line-height: 16px;
  border: 1px solid var(--main-black);
  width: 40%;
  height: 40px;
  cursor: pointer;
  padding-top: 2px;
  margin-bottom: 10px;
}

.cart-bloc {
  display: flex;
  gap: 10px;
  box-sizing: border-box;
}

.cart-bloc button {
  font-family: inherit;
  font-size: inherit;
  color: white;
  background-color: var(--main-black);
  flex: 1;
  border: none;
  cursor: pointer;
  font-weight: bold;
}

.cart-bloc button:hover {
  opacity: 0.7;
}

.cart-bloc div {
  width: 50px;
  height: 50px;
  display: flex;
  justify-content: center;
  align-items: center;
  border: 2px solid var(--main-black);
  color: var(--main-black);
}

.cart-bloc div:hover {
  border-width: 3px;
}

.cart-bloc svg {
  width: 25px;
  height: 25px;
  cursor: pointer;
}
</style>
