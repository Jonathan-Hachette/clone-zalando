<!-- eslint-disable vue/multi-word-component-names -->
<script setup></script>

<template>
  <header>
    <!-- 1er bloc -->
    <div class="headerTop">
      <!-- Wrapper -->
      <div class="container">
        <p>Essayez d'abbord <span>payez après</span></p>
        <p>LIVRAISON & RETOUR <span>GRATUITS*</span></p>
        <p>Retour et <span>remboursement</span></p>
      </div>
    </div>
    <!-- 2ème bloc -->
    <div class="headerBottom">
      <!-- 1er groupe de lien -->
      <div class="container">
        <nav>
          <a>Femme</a>
          <a>Homme</a>
          <a>Enfant</a>
        </nav>
        <img src="../assets/imgs/logo_fcp7ga.svg" alt="logo Zalando" />
        <!-- 2ème groupe de lien -->
        <nav>
          <font-awesome-icon :icon="['far', 'user']" />
          <font-awesome-icon :icon="['far', 'heart']" />
          <font-awesome-icon :icon="['fas', 'shopping-bag']" />
        </nav>
      </div>
    </div>
  </header>
</template>

<style scoped>
.headerTop {
  background-color: var(--light-grey);
}

.headerTop .container {
  display: flex;
  justify-content: space-between;
  align-items: center;
  height: var(--header-top-height);
  color: var(--dark-grey);
  font-size: 12px;
}

span {
  color: var(--main-orange);
}

.headerBottom {
  border-bottom: 1px solid #d0d1d3;
}

.headerBottom .container {
  height: var(--header-bottom-height);
  display: flex;
  justify-content: space-between;
  align-items: center;
}

img {
  width: 155px;
  cursor: pointer;
}

nav {
  display: flex;
  gap: 10px;
  flex: 1;
}

nav a {
  font-weight: bold;
  padding: 10px 15px;
  cursor: pointer;
}

nav a:first-child {
  background-color: var(--main-black);
  color: white;
}

.container nav:nth-child(3) {
  justify-content: flex-end;
}

svg {
  color: var(--main-black);
  padding: 10px;
  /* Pour éviter le décalage de l'icône au moment du survol de la souris, on définit une bordure
  de base. N'hésitez pas à commenter la propriété pour constater la différence */
  border: 2px solid white;
  /* Pour éviter que le padding décale l'icône dans une partie non visible, on doit exclure
  la marge interne et les bordures de la taille du SVG */
  box-sizing: content-box;
  cursor: pointer;
}

svg:hover {
  border: 2px solid var(--main-black);
}
</style>
