<template>
  <!-- Carte individuelle pour afficher les détails d'un Pokémon -->
  <v-card
    :to="`/pokemon/${pokemon.id}`"
    hover
  >
    <v-img
      :src="getImageUrl(pokemon.img)"
      :alt="pokemon.name"
      height="200"
      cover
    />
    <v-card-title>{{ pokemon.name }}</v-card-title>
    <v-card-subtitle>Niveau {{ pokemon.level }}</v-card-subtitle>
  </v-card>
</template>

<script setup>
import { getImageUrl } from '@/utils/imageUrl'

// Définition des propriétés attendues par ce composant
defineProps({
  pokemon: {
    type: Object,
    required: true,
  },
})
</script>
