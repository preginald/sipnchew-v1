<template>
    <v-app-bar app dense>
      <template>
        <v-btn icon to="/"><v-icon>mdi-home</v-icon></v-btn>
      </template>

      <v-spacer></v-spacer>
      <template v-if="nav"> 
        <v-btn icon @click="createNewRecipe()"><v-icon>mdi-plus</v-icon></v-btn>
        <v-btn icon @click="logout()"><v-icon>mdi-logout-variant</v-icon></v-btn>
      </template>
      <template v-else> 
        <v-btn icon to="/login"><v-icon>mdi-login-variant</v-icon></v-btn>
        <!-- <v-btn text to="/register">Sign up</v-btn> -->
      </template>
        <v-btn v-if="$vuetify.theme.dark" icon @click.prevent="toggleDarkMode"><v-icon>mdi-toggle-switch</v-icon></v-btn>
        <v-btn v-else icon @click.prevent="toggleDarkMode"><v-icon>mdi-toggle-switch-off-outline</v-icon></v-btn>
    </v-app-bar>

</template>

<script>

export default {
  name: "Navigation",
  data: () => ({
    nav: true
  }),
  computed: {
  },
  methods: {
    toggleDarkMode(){
      this.$vuetify.theme.dark = !this.$vuetify.theme.dark
      
    }
  },

}; </script>
