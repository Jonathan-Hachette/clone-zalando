<!-- eslint-disable vue/multi-word-component-names -->
<!-- eslint-disable no-unused-vars -->
<script setup>
const props = defineProps({
  productInfo: {
    type: Object,
    required: true
  },
  selectedVariant: {
    type: Object,
    required: true
  }
})

const isVariantSoldOut = (sizes) => {
  //  La boucle 'for in' permet de boucler sur un objet et d'avoir accés aux noms des clés et aux valeurs de celui-ci
  for (const key in sizes) {
    if (sizes[key] > 0) {
      return false
    }
  }

  return true
}
</script>

<template>
  <div>
    <h2>{{ productInfo.brand }}</h2>

    <h1>{{ productInfo.name }}</h1>

    <p>{{ productInfo.price }} € <span>TVA incluse</span></p>

    <div class="rate">
      <font-awesome-icon :icon="['fas', 'star']" size="lg" />
      <font-awesome-icon :icon="['fas', 'star']" size="lg" />
      <font-awesome-icon :icon="['fas', 'star']" size="lg" />
      <font-awesome-icon :icon="['fas', 'star']" size="lg" />
      <font-awesome-icon :icon="['fas', 'star-half-alt']" size="lg" />

      <span>{{ productInfo.rate }}</span>
    </div>

    <p>
      Couleur : <span>{{ selectedVariant.color }}</span>
    </p>

    <div class="img-bloc">
      <img
        v-for="variant in productInfo.variants"
        :key="variant.id"
        :src="variant.image.url"
        :alt="variant.image.alt"
        :class="{
          selectedImg: selectedVariant.id === variant.id,
          outOfStock: isVariantSoldOut(variant.sizes)
        }"
      />
    </div>

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
/* La balise 'p' se trouvant immediatement après la balise 'h1' */
h1 + p {
  font-size: 22px;
  margin-bottom: 25px;
}
h1 + p span {
  color: #66676e;
  font-size: 14px;
  font-weight: lighter;
}

/* -- rate ------- */
.rate {
  margin-bottom: 40px;
}
.rate svg {
  margin-right: 3px;
}

/* -- selected color ------- */
.rate + p {
  font-weight: lighter;
}

.rate + p span {
  font-weight: bolder;
}

/* -- advise ------- */
.advise {
  background-color: #efeff0;
  padding: 20px;
  font-size: 14px;
  line-height: 20px;
  font-weight: lighter;
  margin-bottom: 10px;
}

/* -- cart-bloc ------- */
.cart-bloc {
  display: flex;
  gap: 10px;
}
.cart-bloc button {
  font-family: inherit;
  font-size: inherit;
  font-weight: bold;
  background-color: var(--main-black);
  color: white;
  flex: 1;
  border: none;
  cursor: pointer;
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
  border: 1px solid var(--main-black);
  color: var(--main-black);
}
.cart-bloc div:hover {
  border-width: 2px;
}
.cart-bloc svg {
  width: 25px;
  height: 25px;
  cursor: pointer;
}

/* -- img-bloc ------- */
.img-bloc {
  margin: 10px 0;
  display: flex;
  gap: 10px;
}
img {
  width: 60px;
  height: 70px;
  object-fit: cover;
  cursor: pointer;
}
.selectedImg {
  border: 2px solid black;
}

/* -- sizes -------------------- */
.sizes-bloc {
  display: flex;
  gap: 10px;
  margin-bottom: 10px;
}
.sizes-bloc > div {
  display: flex;
  justify-content: center;
  align-items: center;
  border: 1px solid black;
  width: 40px;
  height: 40px;
  padding-top: 2px;
  cursor: pointer;
}
:is(.sizes-bloc, .img-bloc) .outOfStock {
  /* Syntaxe équivalente à 👇 */
  /*  .sizes-bloc .outOfStock, .img-bloc .outOfStock{ */
  opacity: 0.3;
  cursor: auto;
}
</style>