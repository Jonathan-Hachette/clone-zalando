<!-- eslint-disable no-unused-vars -->
<script setup>
  // Import des composants
  import Header from './components/Header.vue'
  import Footer from './components/Footer.vue'
  import Details from './components/Details.vue'
  import data from './assets/data.json'
  import { reactive } from 'vue'
  import { ref } from 'vue'

  const productInfos = reactive(data)
  const selectedVariant = ref(
    data.variants[0]
  )
</script>

<template>
  <div>
    <Header />

    <main>
      <!-- Wrapper -->
      <div class="container">
        <!-- Première colonne -->
        <div>
          <!-- L'image sera ajoutée dans le chapitre qui lui est dédié -->
        </div>

        <!-- Deuxième colonne -->
        <Details :productInfos="productInfos" :selectedVariant="selectedVariant" />
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
    padding: 25px 0 25px 100px;
  }
</style>