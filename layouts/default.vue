<template>
  <v-app>
    <Header />
    <v-main>
      <v-container fluid>
        <Nuxt />
      </v-container>
    </v-main>
    <Footer />
  </v-app>
</template>

<script>
import { defineComponent } from '@nuxtjs/composition-api'
import Header from '~/components/layouts/Header'
import Footer from '~/components/layouts/Footer'

export default defineComponent({
  components: {
    Header,
    Footer,
  },
  head: {
    title: 'Maxime Leclerc - Front Web Developer',
  },
})
</script>