<template>
  <v-container>
    
    <h2 class="text-h6">
      {{ activeRecipe.name }}
    </h2>

    <v-card class="mb-3">
      <v-card-actions>
        <v-text-field label="servings" v-model="servings"></v-text-field>
      </v-card-actions>
    </v-card>
    <v-card>
      <v-card-title>
        Ingredients
      </v-card-title>
      <v-card-text>
        <v-row>
          <v-col v-for="ingredient in activeRecipe.ingredients" :key="ingredient.name" md="4">
            {{ ingredient.qty * servings }} {{ ingredient.unit }} {{ ingredient.name }}
          </v-col>
        </v-row>
      </v-card-text>
    </v-card>

  </v-container>
</template>

<script>

export default {
  data: () => ({
    servings: 1,
    activeRecipe: {
      name: "Vindaloo",
      ingredients: [
        {unit: "tsp", qty: 1, name: "black peppercorns"},
        {unit: "items", qty: 4, name: "cloves"},
        {unit: "tsp", qty: 2, name: "coriander seeds"},
        {unit: "tsp", qty: 2, name: "fennel seeds"},
        {unit: "tsp", qty: 1, name: "fenugreek seeds"},
        {unit: "items", qty: 2, name: "garlic cloves"},
        {unit: "tbsp", qty: 1, name: "ginger"},
        {unit: "units", qty: 4, name: "dried red chillies"},
        {unit: "tbsp", qty: 1, name: "turmeric powder"},
        {unit: "tsp", qty: 0.5, name: "sea salt"},
        {unit: "tbsp", qty: 1, name: "oil"},
        {unit: "tbsp", qty: 2, name: "tomato puree"},
        {unit: "units", qty: 1, name: "fresh red chillies"},
        {unit: "cup", qty: 1.25, name: "corriander leaves"},
      ]
    }
  }),
}
</script>
