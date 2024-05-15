<script setup>
// Définition des propriétés du composant
// Version simple : const props = defineProps(['troupe', 'or'])
const props = defineProps({
  or: { // Nom de la propriété
    type: Number, // Type de la propriété
    required: true, // Propriété obligatoire
  },
  troupe: {
    type: Object,
    required: true,
  }
})

// Définition des événments du composant
const emit = defineEmits(["former"]);
</script>

<template>
  <article>
    <header :style="`background: linear-gradient(60deg,#3B3B3B 0%, ${troupe.couleur} 100%);`">
      <img :src="troupe.image"
           :alt="troupe.nom">
    </header>
    <div class="level" :style="{color: troupe.couleur}">
      Niveau {{ troupe.niveau }}
    </div>
    <h2 class="name">{{ troupe.nom }}</h2>

    <button
        @click="emit('former', troupe)"
        :style="{backgroundColor: troupe.couleur}"
        :disabled="or < troupe.cout"
    >
      Former <img src="/img/piece-or.png" alt="Former">
    </button>

    <p class="description">{{ troupe.description }}</p>
    <footer>
      <div class="training"
           :style="{backgroundColor: troupe.couleur}">
        <div>{{ troupe.formation }}<sup>sec</sup></div>
        <div>Formation</div>
      </div>
      <div class="speed"
           :style="{backgroundColor: troupe.couleur}">
        <div>{{ troupe.vitesse }}</div>
        <div>Vitesse</div>
      </div>
      <div class="cost"
           :style="{backgroundColor: troupe.couleur}">
        <div>{{ troupe.cout }}</div>
        <div>Coût</div>
      </div>
    </footer>
  </article>
</template>

<style scoped>
/*** Entête Carte Troupe ***/
header {
  height: 230px;
  padding: 0;
  margin-bottom: 35px;
  border-top-left-radius: 14px;
  border-top-right-radius: 14px;
  text-align: center;
}

header img {
  max-width: 400px;
  max-height: 330px;
  margin-top: -65px;
  margin-left: -70px;
}

/*** Contenu Carte Troupe ***/
.level {
  text-transform: uppercase;
  font-size: 12px;
  font-weight: 700;
  margin-bottom: 3px;
}

h2 {
  font-size: 26px;
  color: black;
  font-weight: 900;
  margin-bottom: 5px;
}

button {
  color: white;
  background: #9E9E9E;
  margin: 20px 0 0;
  padding: .75em 1.5em;
}

p.description {
  padding: 20px;
  margin-bottom: 100px;
}

/*** Footer Carte Troupe ***/
footer {
  position: absolute;
  width: 100%;
  bottom: 0;
  color: white;
  font-weight: 700;
  border-bottom-left-radius: 14px;
  border-bottom-right-radius: 14px;
  overflow: hidden;
}

footer > div {
  width: calc(100% / 3);
  float: left;
  padding: 20px 15px;
}

footer sup {
  position: absolute;
  bottom: 4px;
  font-size: 45%;
  margin-left: 2px;
}

footer > div > div:first-child {
  position: relative;
  font-size: 24px;
  margin-bottom: 10px;
}

footer > div > div:first-child + div {
  text-transform: uppercase;
  font-weight: 400;
  font-size: 12px;
}

footer > div {
  border-right: 1px solid rgba(0, 0, 0, .1);
}

footer > div:last-child {
  border-right: none;
}
</style>
