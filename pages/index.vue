<template>
  <div>
    <TheMainPageHeader2></TheMainPageHeader2>
  </div>
</template>

<script>
import TheMainPageHeader2 from '@/components/MainPageComponents/TheMainPageHeader2';

export default {
  head () {
    return {
      title: "Plataforma Verkel | Principal",
      meta: [
        {
          hid: "description",
          name: "description",
          content: "Plataforma de Capacitacion numero uno de Mexico",

        }
      ],
      htmlAtrrs: {
        lang: "es"
      }
    }
  },
  layout: 'default',
  components: {
    TheMainPageHeader2,
  }
}
</script>

