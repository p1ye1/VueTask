<template>
  <v-container fluid class="py-0">
    <v-row align="center" class="fill-height">
      <v-col md="3" sm="6" cols="12" class>
        <v-img
          :src="checkExistance(config.generalConfig.homeImage,0)?config.generalConfig.homeImage:require('@/assets/img/dontremove/codificacion.png')"
          :lazy-src="checkExistance(config.generalConfig.homeImage,0)?config.generalConfig.homeImage:require('@/assets/img/svg/home.svg')"
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
            Universidad Tecnológica <br>Del Oriente De Michoacán<br/>
            <span style="color: #00BD2C;">UTOM</span>
          </b>
        </p>
        <p class="google-font mt-0 mb-0" style="font-size:150%">Somos Tecnologías de Informarción</p>
        <p class="google-font" style="font-size:100%">Trabajamos con lenguajes web, bases de datos y lenguaje de programación.</p>
        <p class="google-font" style="font-size:100%;color:#9e9e9e">
          <span>
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