<template>
  <div class="about">
    <v-btn
      elevation="2"
      @click="pokemonSort('id')"
    >sort by id</v-btn>
    <v-btn
      elevation="2"
      @click="pokemonSort('name')"
    >sort by name</v-btn>
    <v-btn
      elevation="2"
      @click="pokemonSort('type')"
    >sort by type</v-btn>
    <div v-for="(pokemon, index) in pokemons"
        :key="index"
        >
          <pokemon-card :pokemon="pokemon"></pokemon-card>
    </div>
    
  </div>
</template>

<script>
import axios from 'axios';
import PokemonCard from '../components/PokemonCard.vue';
export default {
  components: {
    PokemonCard
  },
  data () {
    return {
      pokemons: []
    }
  },
  mounted () {
    for (let i = 0; i <= 20; i++) {
      axios
      .get(`https://pokeapi.co/api/v2/pokemon/${i}/`)
      .then(response => {
        this.pokemons.push(response.data)
      })
      .catch(e => {
        this.errors.push(e)
      })
    }
  },
  methods: {
    pokemonSort(by) {
      if (by === "id")
        this.pokemons.sort((a, b) => a.id - b.id);
      if (by === "name")
        this.pokemons.sort(function(a, b){
          if(a.name < b.name) { return -1; }
          if(a.name > b.name) { return 1; }
          return 0;});
      if (by === "type")
        this.pokemons.sort(function(a, b){
          if(a.types[0].type.name < b.types[0].type.name) { return -1; }
          if(a.types[0].type.name > b.types[0].type.name) { return 1; }
          return 0;});
    }
  }
}
</script>

<style>

</style>
