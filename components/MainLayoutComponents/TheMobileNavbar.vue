<template>
  <div>
      <v-app-bar
        color="white"
        :flat="$route.path === '/' ? true : false"
    >
      <v-app-bar-nav-icon @click="drawer = true"></v-app-bar-nav-icon>
      <v-spacer></v-spacer>
      <v-toolbar-title>
        <nuxt-link to="/">
          <v-img 
            src="/Logos/verkel-logo.svg"
            width="40" 
          >
          </v-img>
        </nuxt-link>
      </v-toolbar-title>
    </v-app-bar>

    <v-navigation-drawer
      v-model="drawer"
      absolute
      temporary
      height="250px"
    >
      <v-list
        nav
        dense
      >
        <v-list-item-group
          v-model="group"
          active-class="deep-purple--text text--accent-4"
        >
          <v-list-item v-for="link in links" :key="link.name">
            <v-btn 
                  class="ma-10 mt-0 mb-0 menuLinks"
                  elevation="0"
                  text
                  tile
                > 
                  <nuxt-link :to="link.pagina" style="text-decoration: none;">
                    {{ link.name }}
                  </nuxt-link>
            </v-btn>
          </v-list-item>

        </v-list-item-group>
      </v-list>
      <div class="d-flex align-center justify-center mt-3 px-1">
        <v-btn
                  outlined 
                  color="primary" 
                  class="loginBtns" 
                  small
                  @click="loginFormModalView(false)"
                >
                    Registrarse
                </v-btn>
                <v-btn 
                  text 
                  class="loginBtns ml-4" 
                  small
                  @click="loginFormModalView(true)"
                >
                    Iniciar Sesion
                </v-btn>
                <v-dialog
                  width="400"
                  class="d-flex justify-center"
                  v-model="modal"
                  v-if="modal"
                >
                    <div class="d-flex justify-center">
                       <v-card
                        width="400"
                        class="cardLoginForm"
                       >
                          <v-img src="/VerkelLogoMiniToForm.svg" class="imageBehindForm ma-8">
                            <v-card-title v-if="loginFormView" class="d-flex justify-center">
                              <span 
                                class="mr-3 pointerHover"  
                              >
                                  Iniciar Sesion
                              </span>
                              <v-divider vertical></v-divider>
                              <span 
                                class="mr-3 text-subtitle-2 pt-1 pointerHover" 
                                @click="loginFormView = false"
                              >
                                  Registrarse
                              </span>
                            </v-card-title>
                            <v-card-title v-else class="d-flex justify-center">
                              <span 
                                class="mr-4 p-2 text-subtitle-2 pointerHover" 
                                @click="loginFormView = true"
                              >
                                  Iniciar Sesion
                              </span>
                              <v-divider vertical></v-divider>
                              <span 
                                class="span-Registrarse mr-4 p-2 pointerHover"
                              >
                                  Registrarse
                              </span>
                            </v-card-title>
                            <v-divider></v-divider>
                            <v-card-text>
                              <v-expand-transition>
                                <TheLoginForm v-show="loginFormView"></TheLoginForm>
                              </v-expand-transition>
                              <v-expand-transition>
                                <TheRegisterForm v-show="!loginFormView"></TheRegisterForm>
                              </v-expand-transition>
                            </v-card-text>
                          </v-img>
                       </v-card>
                    </div>
                </v-dialog>
      </div>
    </v-navigation-drawer>
  </div>
</template>

<script>

import { mapActions, mapState } from 'vuex';

    export default {
        name: "TheMobileNavbar",
        data() {
            return {
                drawer: false,
                group: null,
                loginFormView: false,
                links: [
                    {
                      key: 'cero',
                      name: 'Principal',
                      pagina: '/',
                    },
                    {
                      key: 'uno',
                      name: 'Blog',
                      pagina: '/blog',
                    },
                    {
                      key:  'dos',
                      name: 'Cursos',
                      pagina: '/cursos',
                    },
                    {
                      key: 'tres',
                      name: 'Para Empresas',
                      pagina: '/',
                    },
                ],
            }
        },
        computed: {
          ...mapState('courses', {
            modal: state => state.loginModal
          }),
        },
        methods: {
          ...mapActions('courses', ['setModalAction']),
          loginFormModalView(e) {
            this.setModalAction(true);
            this.loginFormView = e;
          }
      },
    }
</script>

<style lang="scss" scoped>

.menuLinks {
    padding: 12px 24px;
    background-color: transparent;
    border-radius: 3px;
    position: relative;
    overflow: hidden;
    text-transform: capitalize;
    font-family: 'Roboto', sans-serif;
}

.menuLinks {
    color: #42509e;
    position: relative;
    transition: font-size 0.2s ease-in;
}

</style>