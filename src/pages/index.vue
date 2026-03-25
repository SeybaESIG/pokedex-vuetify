<template>
  <v-container>
    <h1 class="text-h3 text-center my-6">
      Pokédex
    </h1>
    <!-- // Affichage d'une grille de cartes pour chaque Pokémon -->
    <v-row>
      <!-- v-for pour itérer sur la liste des Pokémon et créer une carte pour chacun -->
      <v-col
        v-for="pokemon in pokemons"
        :key="pokemon.id"
        cols="12"
        sm="6"
        md="4"
        lg="3"
      >
        <!-- Affichage des détails de chaque Pokémon -->
        <pokemon-card :pokemon="pokemon" />
      </v-col>
    </v-row>
  </v-container>
</template>

<script setup>
import PokemonCard from "@/components/PokemonCard.vue";

// Variable réactive contenant la liste des Pokémon (tableau vide au départ)
const pokemons = ref([])

// onMounted s'exécute une fois que le composant est affiché dans le navigateur
onMounted(async () => {
  const response = await fetch('http://localhost:3535/pokemons')
  pokemons.value = await response.json()
  console.log('Pokémon chargés :', pokemons.value)
})
</script>
