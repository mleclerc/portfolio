<template>
  <v-app-bar app dark color="primary">
    <v-toolbar-title></v-toolbar-title>
    <v-spacer></v-spacer>
    <v-toolbar-items class="hidden-sm-and-down">
      <v-btn
        v-for="item in navigationItems"
        :key="item.code"
        :to="item.link"
        text
      >
        {{ $t(item.nameI18n) }}
      </v-btn>
      <v-tooltip bottom>
        <template v-slot:activator="{ on, attrs }">
          <v-btn
            :href="github.link"
            target="_blank"
            v-bind="attrs"
            v-on="on"
            icon
          >
            <v-icon>{{ github.icon }}</v-icon>
          </v-btn>
        </template>
        <span>{{ github.link }}</span>
      </v-tooltip>
      <LanguageSwitcher />
    </v-toolbar-items>
    <v-toolbar-items class="hidden-md-and-up">
      <v-menu>
        <template v-slot:activator="{ on, attrs }">
          <v-app-bar-nav-icon v-bind="attrs" v-on="on"></v-app-bar-nav-icon>
        </template>
        <v-list>
          <v-list-item v-for="item in navigationItems" :key="item.code">
            <v-list-item-title>{{ $t(item.nameI18n) }}</v-list-item-title>
          </v-list-item>
        </v-list>
      </v-menu>
    </v-toolbar-items>
  </v-app-bar>
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

    const github = ref({
      username: 'mleclerc',
      icon: 'mdi-github',
      link: 'https://github.com/mleclerc',
    })

    return {
      navigationItems,
      github,
    }
  },
})
</script>
