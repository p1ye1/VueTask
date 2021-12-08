<template>
    <v-container fluid class="">
        <v-row align="center" justify="center">
            <v-col cols="12" md="10" lg="10" sm="12" class="text-center mb-0" >
                <p class="google-font mb-1" style="font-weight: 350;font-size:180%">

                    <b>
                        Mejorando
                        <span style="color: #00BD2C;">Experiencias</span> 
                        &
                        <span style="color: #00BD2C;">Estilo de Vida</span> 
                    </b> 
                </p>
                
                <p class="google-font mt-0" style="font-size:95%">Algunos proyectos de realidad ya sea <strong style="color: #00BD2C;"> ( </strong>virtual<strong style="color: #00BD2C;"> / </strong>aumentada<strong style="color: #00BD2C;"> / </strong>mixta <strong style="color: #00BD2C;"> ) </strong> son ambiciosas y mejoran el estilo de vida implicando también la calidad de vida,
                 como los proyectos que ayudan a tratar el autismo (CicerOn, Proyecto Lancelot) y otros que precervan nuestros patrimonios históricos (Monumenta Salmanticae, Museo Arqueológico Nacional, RV aplicada al turismo),
                 educación inmersiva (como InmersArte y Léeme VR), etc.</p>
                <router-link
                    to="/events"
                    text
                    color="#4C4A78"
                    class="ma-0 google-font mb-0"
                    style="border-radius:5px;text-transform: capitalize;text-decoration:none;color:#4C4A78"
                >Realidad Mixta</router-link>
            </v-col>
            <v-col cols="12" md="12" lg="12" sm="12" class="mt-0 px-0">
               <v-container fluid class="px-2 py-0">
                   <v-row v-if="showLoader" class="">
                       <v-col v-for="i in 4" :key="i" md="3" lg="3" sm="6" cols="6" class="pa-2">
                           <v-sheet
                                :color="`grey ${theme.isDark ? 'darken-2' : 'lighten-4'}`"
                                class=""
                            >
                                <v-skeleton-loader
                                class="mx-auto"
                                type="article"
                                ></v-skeleton-loader>
                            </v-sheet>
                       </v-col>
                   </v-row>
                   <v-row v-else class="no-gutters pa-0 ma-0" >
                       <v-col md="3" lg="3" sm="6" cols="6" class="pa-1 ma-0" v-for="(item,i) in eventsData.slice(0,4)" :key="i">
                           <!-- {{item}} -->
                            <eventCard :data="{data:item}" />
                       </v-col>
                   </v-row>

                   <v-row v-if="notFoundEventFlag">
                       <v-col md="12" lg="12" sm="12" cols="12" class="pa-2 text-center">
                            <v-icon>mdi-close-octagon-outline</v-icon>
                            <p>Events Not Found!</p>
                       </v-col>
                   </v-row>

                

               </v-container>
            </v-col>
        </v-row>
    </v-container>
</template>


<script>
import service from '@/services/appservices'
import eventCard from '@/components/events/UpcomingEventCard'
import { mapState } from 'vuex'
    export default {
        name: 'Eventshome',
        inject: ['theme'],
        components:{
            eventCard
        },
        computed:{
            ...mapState(["config"])
        },
        data: () => ({
            eventsData: [],
            errorMsg:'',
            showLoader: true,
            notFoundEventFlag: false
        }),
        mounted(){
            this.getAllMeetupPastEvents()
        },
        methods:{
            getAllMeetupPastEvents(){
                this.showLoader = true
                service.getAllMeetupPastEvents(this.config.keysandsecurity.meetup).then(res=>{
                    if(res.success){
                        this.eventsData = res.data
                        this.showLoader = false;
                    }else{
                        this.notFoundEventFlag = true;
                        this.showLoader = false;
                    }
                    
                }).catch(e=>{
                    this.errorMsg = "Issue found with " + e;
                    this.showLoader = false;
                })
            }
        }
};
</script>

<style scoped>
   
</style>