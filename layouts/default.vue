<template>
  <v-app>
      <v-app-bar
        id="TheAppBar"
        color="white"
        :flat="$route.path === '/' ? true : false"
        v-if="navbar"
        height="75"
      >
        <TheContentForNavbar></TheContentForNavbar>  
      </v-app-bar>
      <TheMobileNavbar v-else />
      
      <v-main
        id="contentContainer"
        class="overflow-y-auto" 
      >

        <v-container fluid>
          <nuxt  />
        </v-container>

      </v-main>
    
      
      <v-footer 
        id="TheFooter"
        class="mt-16"
        color="rgba(119, 119, 119, 0.1)"
      >
        <TheContentForFooter></TheContentForFooter>
      </v-footer>
    </v-app>
</template>

<script>
import TheContentForNavbar from '@/components/MainLayoutComponents/TheContentForNavbar';
import TheContentForFooter from '@/components/MainLayoutComponents/TheContentForFooter'
import TheMobileNavbar from '@/components/MainLayoutComponents/TheMobileNavbar'

export default {
  components: {
    TheContentForNavbar,
    TheContentForFooter,
    TheMobileNavbar
  },
  computed: {
    mobileNavbar() {
      switch (this.$vuetify.breakpoint.name) {
        case 'xs': return true
        case 'sm': return true
        case 'md': return false
        case 'lg': return false
        case 'xl': return false
      }
    },
    navbar() {
      switch (this.$vuetify.breakpoint.name) {
        case 'xs': return false
        case 'sm': return false
        case 'md': return true
        case 'lg': return true
        case 'xl': return true
      }
    },
  },
}
</script>

<style>
#TheAppBar{
  z-index: 1;
}

.theme--light.v-application{
  background-image: linear-gradient(to left, var(--v-firstbackground-base), var(--v-secondbackground-base)) !important;;
}

.v-bottom-navigation #TheBottomNav{
  opacity: 0.1;
}

.verkelTransitionPages-enter-active, .home-leave-active {
  transition: .5s;
}

.verkelTransitionPages-enter, .verkelTransitionPages-active {
  opacity: 0;
}

</style>
