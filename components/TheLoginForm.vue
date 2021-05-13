<template>
    <div>
        <v-form class="mt-8 loginForm">
            <v-row>
                <v-col cols="12">
                    <v-text-field 
                      class=""
                      type="email"
                      single-line
                      v-model="formData.email"
                      placeholder="Correo Electronico"
                      dense
                    />
                </v-col>
                <v-col cols="12">
                    <v-text-field
                      class=""
                      :type="showPassword ? 'text' : 'password' "
                      :append-icon="showPassword ? 'mdi-eye mb-1' : 'mdi-eye-off mb-1' " 
                      @click:append=" showPassword = !showPassword "
                      single-line
                      v-model="formData.password"
                      placeholder="Contraseña"
                      dense
                    />
                </v-col>
                <v-col cols="12 d-flex justify-center">
                    <v-btn color="primary" x-small text style="text-transform: capitalize;">¿Nuevo?, Registrate Ahora</v-btn>
                </v-col>
                <v-alert
                    dismissible
                    :value="loginAlert"
                    color="#FFB74D"
                    dark
                    transition="scale-transition"
                    style="font-family: Roboto;"
                    class="text-center text-subtitle-2 text-lg-caption"
                >
                    El Inicio de Sesion no esta disponible por el momento.
                </v-alert>
            </v-row>
        </v-form>
        <v-divider></v-divider>
        <v-card-actions class="d-flex justify-center">
            <v-btn color="primary" class="mt-8" type="submit" small @click="loginAlert = !loginAlert">Iniciar Sesion</v-btn>
            <v-btn color="error" class="ml-4 mt-8" small outlined @click="setModalAction(false)">Cancelar</v-btn>
        </v-card-actions>
    </div>
</template>

<script>

import { mapActions } from 'vuex';

export default {
    name: "TheLoginForm",
    data () {
        return {
            loginAlert: false,
            showPassword: false,
            formData: {
                email: "",
                password: "",
            },
        }
    },
    methods: {
         ...mapActions('courses', ['setModalAction']),
    }
}

</script>

<style scoped>

</style>