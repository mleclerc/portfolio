<template>
  <v-footer app padless>
    <v-col class="text-center">
      <strong>&copy; {{ new Date().getFullYear() }}</strong> — Maxime Leclerc
    </v-col>
  </v-footer>
</template>

<script>
import { defineComponent } from '@vue/composition-api'

export default defineComponent({
  setup() {},
})
</script>
