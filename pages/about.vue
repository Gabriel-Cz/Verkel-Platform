<template>
    <div>
        <v-container class="d-flex justify-center">
            <v-card :width="cardWidth" outlined class="my-16 pa-8 d-flex justify-center flex-column" color="transparent" elevation="20">
                <div class="d-flex justify-center text-center">
                    <p class="text-body-1 text-center">
                        Verkel es un prototipo desarollado con fines de introduccion para la cual en algun futuro, seria una plataforma de <strong>Capacitacion</strong> enfocada en <strong>Capital Humano</strong>.
                    </p>
                </div>
                <div class="mt-10">
                    <v-img class="mx-auto" :width="this.$vuetify.breakpoint.name === 'xs' ? '40%' : '25%'" src="./Logos/verkel-logo-animation.svg"></v-img>
                </div>
            </v-card>
        </v-container>
    </div>
</template>

<script>
    export default {
        head() {
            return {
                title: "Plataforma Verkel | Acerca De"
            }
        },
        computed: {
            cardWidth() {
                switch (this.$vuetify.breakpoint.name) {
                    case 'xs': return "100%"
                    case 'sm': return "50%"
                    case 'md': return "50%"
                    case 'lg': return "40%"
                    case 'xl': return "25%"
                }
            }
        }
    }
</script>
