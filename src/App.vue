<script setup>
// Cheat Sheet: https://steve-fallet.notion.site/Vue-3-script-setup-Cheat-Sheet-b12192ceae244ecda65f771579ca02bc
import {onMounted, ref} from 'vue'
import PageTopBarre from "@/components/PageTopBarre.vue";
import PageHeader from "@/components/PageHeader.vue";
import PageFooter from "@/components/PageFooter.vue";
import TroupeCarte from "@/components/TroupeCarte.vue";

// Tableau des troupes
const troupes = ref([])
// Pièces d'or
let totalOr = ref(100000);

// troupes.value[0].nom = "toto"
// console.log(troupes.value[0].nom)

// Quand le composant est monté, on va chercher les données
onMounted(() => {
  // Fecth est une fonction asynchrone qui permet de faire des requêtes HTTP
  fetch('https://cocapi.divtec.me/troupes') // Appel à l'API
      .then(function (reponseAPI) { return  reponseAPI.json() }) // On récupère les données en JSON et on les transforme en objet JavaScript
      .then((donneesAuFormatJS) => { // On récupère les données au format JavaScript
        troupes.value = donneesAuFormatJS // On les stocke dans la variable troupes
      })
})

</script>

<template>
  <PageTopBarre :or="totalOr" />
  <PageHeader />
  <main>
    <ul class="cartes">
      <li v-for="troupe in troupes">
          <TroupeCarte :troupe="troupe" :or="totalOr" />
      </li>
    </ul>
  </main>
  <PageFooter />
</template>

<style scoped>

</style>
