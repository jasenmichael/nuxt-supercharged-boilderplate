<template>
  <v-app dark>
    <v-navigation-drawer v-model="drawer" :clipped="clipped" fixed app>
      <v-list>
        <v-list-item
          v-for="(item) in items"
          :key="item.title"
          :to="item.to"
          router
          exact
        >
          <v-list-item-action>
            <v-icon>{{ item.icon }}</v-icon>
          </v-list-item-action>
          <v-list-item-content>
            <v-list-item-title v-text="item.title" />
          </v-list-item-content>
        </v-list-item>
        <!-- admin -->
        <v-list-item :href="`./admin`">
          <v-list-item-action>
            <v-icon>{{ icons.mdiCog }}</v-icon>
          </v-list-item-action>
          <v-list-item-content>
            <v-list-item-title> Admin </v-list-item-title>
          </v-list-item-content>
        </v-list-item>
        <hr />
        <v-list-item
          v-for="(item) in social"
          :key="item.name"
          :href="item.href"
          target="_blank"
        >
          <v-list-item-action>
            <v-icon>{{ item.icon }}</v-icon>
          </v-list-item-action>
          <v-list-item-content>
            <v-list-item-title v-text="item.title" />
          </v-list-item-content>
        </v-list-item>
      </v-list>
    </v-navigation-drawer>

    <v-app-bar :clipped-left="clipped" fixed app>
      <v-btn icon @click.stop="drawer = !drawer">
        <v-icon> {{ icons.mdiMenu }} </v-icon>
      </v-btn>
      <!-- <v-app-bar-nav-icon @click.stop="drawer = !drawer" /> -->
      <v-toolbar-title v-text="$config.siteData.name" />
      <v-spacer />
    </v-app-bar>

    <v-main>
      <v-container>
        <nuxt />
      </v-container>
    </v-main>

    <v-footer :absolute="!fixed" app>
      <span>&copy; {{ new Date().getFullYear() }}</span>
    </v-footer>
  </v-app>
</template>

<script>
import {
  mdiApps,
  mdiChartBubble,
  mdiCog,
  mdiMenu,
  mdiContacts,
  mdiTwitter,
  mdiFacebook,
} from '@mdi/js'

export default {
  data: () => ({
    // return {
    icons: {
      mdiApps,
      mdiChartBubble,
      mdiCog,
      mdiMenu,
      mdiContacts,
      mdiTwitter,
      mdiFacebook,
    },
    clipped: true,
    drawer: false,
    fixed: false,
    items: [
      {
        icon: mdiApps,
        title: 'Welcome',
        to: '/',
      },
      {
        icon: mdiChartBubble,
        title: 'About',
        to: '/about',
      },
      {
        icon: mdiContacts,
        title: 'Contact',
        to: '/contact',
      },
    ],
  }),
  computed: {
    social() {
      return this.$config.siteData.networks.map((network) => {
        return {
          name: network.name,
          title: '@' + network.handle,
          href: network.url,
          icon: this.icon(network.name),
        }
      })
    },
  },
  methods: {
    icon(name) {
      let icon
      switch (name) {
        case 'Twitter':
          return this.icons.mdiTwitter
        case 'Facebook':
          return this.icons.mdiFacebook
        default:
          return
      }
    },
  },
}
</script>
