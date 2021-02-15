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
    <v-card class="mb-3">
      <v-card-title>
        Ingredients
      </v-card-title>
      <v-card-text>
        <v-row>
          <v-col v-for="ingredient in activeRecipe.ingredients" :key="ingredient.name" cols="12" xs="12" sm="6" md="4">
            <v-checkbox v-model="ingredient.status" :label="ingredientLabel(ingredient)"></v-checkbox>
          </v-col>
        </v-row>
      </v-card-text>
    </v-card>

    <v-row>
      <v-col v-for="step in activeRecipe.steps" :key="step.title" cols="12" xs="12" sm="12" md="4">
        <v-card>
          <v-card-title>{{ step.title }}</v-card-title>
          <v-card-text v-for="task in step.tasks" :key="task.title">
            <v-checkbox v-model="task.status" :label="task.title"></v-checkbox>
          </v-card-text>
        </v-card>
      </v-col>
    </v-row>

  </v-container>
</template>

<script>

export default {
  data: () => ({
    servings: 1,
    settings: [],
    activeRecipe: {
      name: "Vindaloo paste",
      ingredients: [
        {active: false, unit: "tsp", qty: 1, name: "black peppercorns"},
        {active: false, unit: "items", qty: 4, name: "cloves"},
        {active: false, unit: "tsp", qty: 2, name: "coriander seeds"},
        {active: false, unit: "tsp", qty: 2, name: "fennel seeds"},
        {active: false, unit: "tsp", qty: 1, name: "fenugreek seeds"},
        {active: false, unit: "items", qty: 2, name: "garlic cloves"},
        {active: false, unit: "tbsp", qty: 1, name: "ginger"},
        {active: false, unit: "units", qty: 4, name: "dried red chillies"},
        {active: false, unit: "tbsp", qty: 1, name: "turmeric powder"},
        {active: false, unit: "tsp", qty: 0.5, name: "sea salt"},
        {active: false, unit: "tbsp", qty: 1, name: "oil"},
        {active: false, unit: "tbsp", qty: 2, name: "tomato puree"},
        {active: false, unit: "units", qty: 1, name: "fresh red chillies"},
        {active: false, unit: "cup", qty: 1.25, name: "corriander leaves"},
      ],
      steps: [
        { title: "Put frying pan on medium to high heat" },
        { title: "Add the following to the frying pan.", 
          tasks: [
          { title: "black peppercorns", status: false },
          { title: "cloves", status: false },
          { title: "coriander seeds", status: false },
          { title: "fenugreek seeds", status: false },
        ]},
        { title: "Lightly toast the spices for 7 minutes", description: "Spices will turn golden brown and smelling toasty."},
        { title: "Remove frying pan from the heat" },
        { title: "Blend the toasted ingredients", 
          tasks: [
          { title: "Add the toasted ingredients to a blender or mortar" },
          { title: "Grind until fine powder" },
        ]},
        { title: "Blend the remaining ingredients", 
          tasks: [
          { title: "Add the toasted ingredients to a blender or mortar" },
          { title: "Grind until a smooth paste consistancy" },
        ]},
      ]
    }
  }),
  methods: {
    ingredientLabel(ingredient){
      return ingredient.qty * this.servings + " " + ingredient.unit + " " + ingredient.name
    }
  }
}
</script>
