<template>
        <v-container fluid class="footerContainer">
            <v-row justify="center" align="center">
                <v-col cols="12" md="3" sm="3" lg="4" class="d-flex justify-center">
                    <div>
                        <v-icon 
                          v-for="icon in footerIcons"
                          :key="icon.name"
                          class="ma-6 mt-2"
                        >
                                {{ icon.name }}
                        </v-icon>
                    </div>
                </v-col>
                <v-col cols="12" md="4" sm="4" lg="4"> 
                    <div class="borders text-subtitle-1 informationBorders">
                        <p class="pt-2 pl-4"><em>Contactanos:</em> {{ information.email }}</p>
                        <p class="mt-1 pl-4"><em>Telefono: +</em> {{ information.telNumber }}</p>
                    </div>
                </v-col>
                <v-col cols="12" md="5" sm="5" lg="4">
                    <div class="borders descriptionBorders text-subtitle-1">
                        <p class="pt-2 "><em>Sobre Verkel:</em> {{ information.verkelDescription }}</p>
                    </div>
                </v-col>
                <v-col class="d-flex justify-center align-center py-2">
                    <small><v-avatar size="16" class="mr-2"><v-img src="/Logos/verkel-logo.svg"></v-img></v-avatar> Verkel - 2020</small>
                </v-col>
           </v-row>
        </v-container>
    
</template>

<script>
export default {
    name: "TheContentForFooter",
    data () {
        return {

            footerIcons: [
               {
                  name: "mdi-twitter"
               },
               {
                  name: "mdi-instagram"
               },
               {
                  name: "mdi-email",
               }
            ],
           information: {
               email: "plataformaverkel@verkel.com",
               telNumber: "442 2445 555",
               verkelDescription: "Prototipo desarollado, basado en una Plataforma de Capacitacion Latinoamericana enfocada en el campo del Capital Humano."
           }
        }
    }
}
</script>

<style scoped>

.footerContainer {
    border-top: solid 1px rgba(128, 128, 128, 0.5);
}

</style>