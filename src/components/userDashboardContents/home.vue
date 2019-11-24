<template>
<v-container>
  <v-row align="center" justify="center">
    <v-img
      src="../../assets/home1.png"
      aspect-ratio="1"
      class="mx-auto"
      max-height="400"
    ></v-img>
  </v-row>
  
<v-row no-gutters style="margin-top: 30px; margin-bottom: 100px">
      <v-col order="last" style="margin: 10px">
        <v-card
          class="mx-auto"
        >
         <v-img
          src="../../assets/children.jpg"
          aspect-ratio="1"
          class="grey lighten-2"
          max-height="500"
        ></v-img>
        </v-card>
      </v-col>
      <v-col style="margin: 10px">
        <v-card
          class="mx-auto"
        >
         <v-img
          src="../../assets/women.jpg"
          aspect-ratio="1"
          class="grey lighten-2"
          max-height="500"
        ></v-img>
        </v-card>
      </v-col>
      <v-col order="first" style="margin: 10px">
        <v-card
          class="mx-auto"
        >
          <v-img
          src="../../assets/men.jpg"
          aspect-ratio="1"
          class="grey lighten-2"
          max-height="500"
        ></v-img>
        </v-card>
      </v-col>
    </v-row>

    <v-footer
      absolute
      class="font-weight-medium"
    >
      <v-col
        class="text-center"
        cols="12"
      >
        {{ new Date().getFullYear() }} — <strong>Vychomena</strong>
      </v-col>
    </v-footer>
</v-container>
</template>