<template>
<v-app>
  <!-- <v-navigation-drawer app>

  </v-navigation-drawer> -->

  <v-app-bar app
  color="indigo darken-2"
  dark
  shrink-on-scroll
  src="https://cdn.vuetifyjs.com/images/backgrounds/vbanner.jpg"
  prominent
  fade-img-on-scroll>
    <v-toolbar-title>Pokédex</v-toolbar-title>
    <v-spacer></v-spacer>
    <v-btn icon>
          <v-icon>fas fa-search</v-icon>
        </v-btn>
  </v-app-bar>

  <!-- Sizes your content based upon application components -->
  <v-main>

    <!-- Provides the application the proper gutter -->
    <v-container fluid>

      <!-- If using vue-router -->
      <router-view></router-view>
    </v-container>
  </v-main>

  <v-footer app>
    <!-- -->
  </v-footer>
</v-app>
</template>

<script>

export default {
  name: "App",

  data: () => ({
    //
  })
};
</script>
<style>
</style>
