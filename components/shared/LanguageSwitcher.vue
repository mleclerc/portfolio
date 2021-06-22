<template>
  <v-toolbar-items>
    <v-tooltip v-for="locale in availableLocales" :key="locale.code" bottom>
      <template v-slot:activator="{ on, attrs }">
        <v-btn
          :to="switchLocalePath(locale.code)"
          v-bind="attrs"
          v-on="on"
          icon
        >
          <img width="30" :src="locale.flagPath" />
        </v-btn>
      </template>
      <span>{{ locale.name }}</span>
    </v-tooltip>
  </v-toolbar-items>
</template>

<script>
import { defineComponent, computed, useContext } from '@nuxtjs/composition-api'

export default defineComponent({
  setup() {
    const { i18n } = useContext()

    const availableLocales = computed(() => {
      return i18n.locales.filter((locale) => locale.code !== i18n.locale)
    })

    return { availableLocales }
  },
})
</script>
