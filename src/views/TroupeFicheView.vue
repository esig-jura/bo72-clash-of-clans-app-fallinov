<script setup>
import { useRoute } from "vue-router";
// Récupérer un paramètre de l'URL (de route)
const route = useRoute();
console.log(route.params.id)
</script>

<template>
    <h1>Troupe n° {{ route.params.id }}</h1>
</template>

<style>

</style>
