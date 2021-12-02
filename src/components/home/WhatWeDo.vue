<template>
  <v-container fluid>
    <v-row align="center" justify="center">
      <v-col cols="12" md="3" lg="3" sm="4" class>
        <p class="google-font mb-0" style="font-size:150%">¡Construye tu realidad!</p>
        <p
          class="google-font mt-0"
          style="font-size:95%"
        >La realidad aumentada mejora las experiencias al agregar componentes virtuales como imágenes digitales,
         gráficos o sensaciones como una nueva capa de interacción con el mundo real. En contraste, la realidad 
         virtual crea su propio mundo, que está completamente generado e impulsado por ordenador.</p>
        <p class="google-font" style="font-size:95%">Acerca de VR & AR technologies.</p>
        <span v-for="(item,i) in whatwedodata" :key="i">
          <v-tooltip bottom>
            <template v-slot:activator="{ on }">
              <a :href="item.link" target="_blank" class="ma-0 mx-3" rel="noreferrer">
                <img :src="getImgUrl(item.image)" width="25vh" alt srcset dark v-on="on" />
              </a>
              &nbsp;&nbsp;&nbsp;
            </template>
            <span>{{item.TechName}}</span>
          </v-tooltip>
        </span>
      </v-col>
      <v-col cols="12" md="9" lg="9" sm="8">
        <v-container fluid>
          <v-row>
            
            <v-col md="3" lg="3" sm="6" cols="6" class="text-center pa-2">
              <v-icon large style="font-size:300%">mdi-comment</v-icon>
              <p class="google-font mt-2" style="font-size:130%">ARKit</p>
              <p
                class="google-font"
                style="font-size:95%"
              >Las innovadoras plataformas ARKit y RealityKit desarrollan y crean 
              experiencias de realidad aumentada para el iPhone, el iPad y el iPod touch</p>
            </v-col>

            <v-col md="3" lg="3" sm="6" cols="6" class="text-center pa-2">
              <v-icon large style="font-size:300%">mdi-code-tags</v-icon>
              <p class="google-font mt-2" style="font-size:130%">AR Core</p>
              <p
                class="google-font"
                style="font-size:95%"
              >Con ARCore, cree nuevas experiencias de realidad aumentada
              que combinen a la perfección los mundos digital y físico</p>
            </v-col>

            <v-col md="3" lg="3" sm="6" cols="6" class="text-center pa-2">
              <v-icon large style="font-size:300%">mdi-school</v-icon>
              <p class="google-font mt-2" style="font-size:130%">Oculus</p>
              <p
                class="google-font"
                style="font-size:95%"
              >Ofrece al usuario experiencias de realidad virtual, aumentada y mixta que funcionen bien</p>
            </v-col>

            <v-col md="3" lg="3" sm="6" cols="6" class="text-center pa-2">
              <v-icon large style="font-size:300%">mdi-chart-bubble</v-icon>
              <p class="google-font mt-2" style="font-size:130%">Live Viewing Parties</p>
              <p
                class="google-font"
                style="font-size:95%"
              >Comparte tus conocimientos en diferentes compañías, colegios y universidades (Online)</p>
            </v-col>

          </v-row>
        </v-container>
      </v-col>
    </v-row>
  </v-container>
</template>

<script>
import whatwedodata from "@/assets/data/whatwedo.json";
export default {
  name: "App",
  data: () => ({
    whatwedodata: whatwedodata
  }),
  methods: {
    getImgUrl(url) {
      if (url.length > 0) {
        return require("@/assets/img/what-we-do/" + url);
      } else {
        return require("@/assets/img/what-we-do/notFound.png");
      }
    }
  }
};
</script>