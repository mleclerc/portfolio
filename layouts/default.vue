<template>
    <v-app>
      <Header />
      <v-main>
        <Nuxt />
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