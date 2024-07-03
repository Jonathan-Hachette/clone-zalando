<!-- eslint-disable vue/multi-word-component-names -->
<!-- eslint-disable no-unused-vars -->

<script setup>
const props = defineProps({
  productInfos: {
    type: Object,
    required: true
  },
  selectedVariant: {
    type: Object,
    required: true
  }
})
</script>

<template>
  <div class="details">
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
    <p>
      Couleur : <span class="selectedColor">{{ selectedVariant.color }}</span>
    </p>

    <p class="advise">
      Nous vous recommandons de choisir une taille au-dessus de celle habituelle.
    </p>
    <div class="sizes-bloc">
      <div
        v-for="(quantity, size) in selectedVariant.sizes"
        :key="size"
        :class="{
          outOfStock: quantity === 0
        }"
      >
        {{ size }}
      </div>
    </div>
    <div class="cart-bloc">
      <button>Ajouter au panier</button>
      <div>
        <font-awesome-icon :icon="['far', 'heart']" />
      </div>
    </div>
  </div>
</template>

<style scoped>
.details {
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

.selectedColor {
  font-weight: bold;
}

.advise {
  background-color: var(--light-grey);
  padding: 20px;
  font-size: 14px;
  line-height: 20px;
  font-weight: lighter;
  margin-bottom: 10px;
}

.sizes-bloc {
  display: flex;
  gap: 10px;
}

.sizes-bloc > div {
  display: flex;
  justify-content: center;
  align-items: center;
  border: 1px solid var(--main-black);
  width: 40px;
  height: 40px;
  padding-top: 2px;
  cursor: pointer;
  margin-bottom: 10px;
}

.sizes-bloc .outOfStock {
  opacity:0.3;
  cursor: auto;
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
