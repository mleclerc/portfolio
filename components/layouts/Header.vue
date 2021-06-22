<template>
  <v-toolbar height="60" color="primary">
    <v-toolbar-title></v-toolbar-title>
    <v-spacer></v-spacer>
    <v-toolbar-items class="hidden-sm-and-down">
      <v-btn
        class="white--text"
        v-for="item in navigationItems"
        :key="item.code"
        :to="item.link"
        text
      >
        {{ $t(item.nameI18n) }}
      </v-btn>
    </v-toolbar-items>
    <LanguageSwitcher />
    <v-menu class="hidden-sm-and-up">
      <template v-slot:activator="{ on, attrs }">
        <v-app-bar-nav-icon v-bind="attrs" v-on="on"></v-app-bar-nav-icon>
      </template>
      <v-list>
        <v-list-item v-for="item in navigationItems" :key="item.code">
          <v-list-item-title>{{ $t(item.nameI18n) }}</v-list-item-title>
        </v-list-item>
      </v-list>
    </v-menu>
  </v-toolbar>
</template>

<script>
import LanguageSwitcher from '~/components/shared/LanguageSwitcher'
import { defineComponent, ref } from '@nuxtjs/composition-api'

export default defineComponent({
  components: {
    LanguageSwitcher,
  },
  setup() {
    const navigationItems = ref([
      { code: 'about', nameI18n: 'common.header.about' },
      { code: 'experience', nameI18n: 'common.header.experience' },
      { code: 'skills', nameI18n: 'common.header.skills' },
      { code: 'blog', nameI18n: 'common.header.blog' },
      { code: 'contact', nameI18n: 'common.header.contact' },
    ])

    return {
      navigationItems,
    }
  },
})
</script>
