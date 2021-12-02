<template>
  <v-container fluid class="py-0">
    <v-row align="center" class="fill-height">
      <v-col md="3" sm="6" cols="12" class>
        <v-img
          :src="checkExistance(config.generalConfig.homeImage,0)?config.generalConfig.homeImage:require('@/assets/img/dontremove/realidad_aumentada.png')"
          :lazy-src="checkExistance(config.generalConfig.homeImage,0)?config.generalConfig.homeImage:require('@/assets/img/dontremove/realidad_aumentada.png')"
          width="100%"
        >
          <template v-slot:placeholder>
            <v-row class="fill-height ma-0" align="center" justify="center">
              <v-progress-circular indeterminate color="grey lighten-5"></v-progress-circular>
            </v-row>
          </template>
        </v-img>
      </v-col>
      <v-col md="9" sm="6" cols="12" class="px-0">
        <p
          class="google-font mb-1"
          :class="$vuetify.theme.dark == true?'dark-font-color':'light-font-color'"
          style="font-weight: 350;font-size:230%"
        >
          <b>
            <span style="color: #00BD2C;">UTOM</span>
            Realidad Virtual & Realidad Aumentada 
          </b>
        </p>
        <p class="google-font mt-0 mb-0" style="font-size:150%">¿Cuál es la diferencia?</p>
        <p class="google-font mb-1" style="font-size:100%;color:#9e9e9e"> Mientras que la <strong style="font-size:100%;color:#00BD2C">Realidad Virtual</strong> permite crear un mundo virtual desde cero con todo lo que queramos, pero un mundo fantástico. 
        <br>Lo que hace la <strong style="font-size:100%;color:#00BD2C">Realidad Aumentada</strong> es agregar elementos virtuales (información adicional en forma de gráficos o imágenes) a nuestro entorno real.</p>
        <p class="google-font" style="font-size:100%;color:#9e9e9e">
          <span>
            <v-chip
              :href="'https://twitter.com/hashtag/vr'"
              rel="noreferrer"
              target="_blank"
              small
              class="mr-1"
            >#VR</v-chip>
            <v-chip
              :href="'https://twitter.com/hashtag/ar'"
              rel="noreferrer"
              target="_blank"
              small
              class="mr-1"
            >#AR</v-chip>
            <v-chip
              :href="'https://twitter.com/hashtag/estudiambre'"
              rel="noreferrer"
              target="_blank"
              small
              class="mr-1"
            >#EstudiHambre</v-chip>
            <v-chip
              :href="'https://twitter.com/hashtag/somosutom'"
              rel="noreferrer"
              target="_blank"
              small
              class="mr-1"
            >#somosUTOM</v-chip>
            <!-- &nbsp; -->
          </span>
        </p>

        <v-btn
          v-if="checkExistance(config.generalConfig.becomemember,0)"
          :href="config.generalConfig.becomemember"
          target="_blank"
          rel="noreferrer"
          aria-label="Become a Member"
          class="ma-0 google-font elevation-1 success mr-2"
          style="text-transform: capitalize;border-radius:5px;color:white"
        >Vuelvélte Miembro</v-btn>
        <v-btn
          v-if="checkExistance(config.generalConfig.learnMoreLink,0)"
          :href="config.generalConfig.learnMoreLink"
          target="_blank"
          aria-label="Learn More"
          rounded
          rel="noreferrer"
          color="green"
          style="text-transform: capitalize;border-radius:5px;text-transform: capitalize;"
          outlined
          class="ml-0"
          dark
        >Aprénde Más</v-btn>
      </v-col>
    </v-row>
  </v-container>
</template>

<script>
import { mapState } from "vuex";

export default {
  data: () => ({}),
  computed: {
    ...mapState(["config"])
  }
};
</script>

<style scoped>
.dark-font-color {
  color: white;
}
.light-font-color {
  color: #616161;
}
</style>