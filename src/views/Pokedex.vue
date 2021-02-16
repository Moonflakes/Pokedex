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
    <input class="form-control" type="text" v-model="searchName" placeholder="Search by name" />
    <input class="form-control" type="text" v-model="searchType" placeholder="Search by type" />
    <div v-for="(pokemon, index) in filteredPokemons"
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
      pokemons: [],
      searchName: null,
      searchType: null
    }
  },
  computed: {
    filteredPokemons(){
      if(this.searchName){
        return this.pokemons.filter((pokemon)=>{
          return this.searchName.toLowerCase().split(' ').every(v => pokemon.name.toLowerCase().includes(v))
      })
      }else if(this.searchType){
        return this.pokemons.filter((pokemon)=>{
          return this.searchType.toLowerCase().split(' ').every(v => pokemon.types[0].type.name.toLowerCase().includes(v))
        })
      }
      else{
        return this.pokemons;
      }
    }
  },
  mounted () {
    for (let i = 1; i <= 20; i++) {
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
