<template>
  <div class="about">
    <div v-for="(pokemon, index) in pokemons"
        :key="index">
          <v-card
            class="mx-auto"
            max-width="344"
            outlined
          >
            <v-list-item three-line>
              <v-list-item-content>
                <h4>
                  {{pokemon.name}}
                </h4>
                <v-list-item-subtitle>
                  id: {{pokemon.id}}
                </v-list-item-subtitle>
                <v-list-item-subtitle>
                  type: {{pokemon.types[0].type.name}}
                </v-list-item-subtitle>
                <v-list-item-subtitle>
                  height: {{pokemon.height}}
                </v-list-item-subtitle>
                <v-list-item-subtitle>
                  weight: {{pokemon.weight}}
                </v-list-item-subtitle>
                <v-list-item-subtitle>
                  abilities: {{pokemon.abilities[0].ability.name}}
                </v-list-item-subtitle>
              </v-list-item-content>

              <v-list-item-avatar
              ><img
                :src="pokemon.sprites.front_default"
              ></v-list-item-avatar>
            </v-list-item>

            <!-- <v-card-actions>
              <v-btn
                outlined
                rounded
                text
              >
                Button
              </v-btn>
            </v-card-actions> -->
          </v-card>
    </div>
    
  </div>
</template>

<script>
import axios from 'axios';
// import { PokemonCard } from '@/components/PokemonCard.vue';
export default {
  // components: {
  //   PokemonCard
  // },
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
    
  }
}
</script>

<style>

</style>
