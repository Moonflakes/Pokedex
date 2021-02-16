<template>
<v-card
            class="mx-auto"
            max-width="344"
            outlined
            @click="overlay = !overlay"
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
              </v-list-item-content>

              <v-list-item-avatar
              ><img
                :src="pokemon.sprites.front_default"
              ></v-list-item-avatar>
            </v-list-item>

      <v-overlay :value="overlay">
                <v-card
      class="mx-auto my-12"
      max-width="374"
    >
      <template slot="progress">
        <v-progress-linear
          color="deep-purple"
          height="10"
          indeterminate
        ></v-progress-linear>
      </template>
  
      <v-img
        height="250"
        :src="pokemon.sprites.front_default"
      ></v-img>
  
      <v-card-title>pokemon.name</v-card-title>
  
      <v-card-text>
        <div class="my-1 subtitle-1">
          id: {{pokemon.id}}
        </div>
        <div class="my-1 subtitle-1">
          type: {{pokemon.types[0].type.name}}
        </div>
  
        <div>height: {{pokemon.height}}</div>
        <div>weight: {{pokemon.weight}}</div>
        <div>abilities: {{pokemon.abilities[0].ability.name}}</div>
      </v-card-text>
  
    </v-card>
        </v-overlay>
          </v-card>

</template>

<script>
    export default {
        props: {
            pokemon: {
                type: Object,
            }
        },
        data: () => ({
            overlay: false
        }),
    }
</script>

<style lang="scss" scoped>

</style>