<template>
  <v-app>
    <v-navigation-drawer
      v-model="sideDrawer"
      fixed
      app
    >
      <v-list>
        <v-list-item
          v-for="(item, i) in sideMenus"
          :key="i"
          :to="item.to"
          router
          exact
        >
          <v-list-item-action>
            <v-icon>{{ item.icon }}</v-icon>
          </v-list-item-action>
          <v-list-item-content>
            <v-list-item-title>{{ item.title }}</v-list-item-title>
          </v-list-item-content>
        </v-list-item>
      </v-list>
    </v-navigation-drawer>

    <v-main>
      <v-container>
        <Nuxt />
      </v-container>
    </v-main>

    <v-bottom-navigation app horizontal height="10vh" fixed color="primary">
      <v-app-bar-nav-icon v-ripple="false" plain @click.stop="sideDrawer = !sideDrawer" />
      <v-btn
        v-for="(item, i) in bottomMenus"
        :key="i"
        v-ripple="false"
        :to="item.to"
        plain
      >
        <span>{{ item.title }}</span>
        <v-icon>{{ item.icon }}</v-icon>
      </v-btn>
      <v-spacer />
    </v-bottom-navigation>
  </v-app>
</template>

<script>
export default {
  name: 'DefaultLayout',
  data () {
    return {
      sideDrawer: false,
      sideMenus: [
        {
          icon: 'mdi-account',
          title: 'Account',
          to: '/account'
        },
        {
          icon: 'mdi-bell',
          title: 'Notification',
          to: '/notification'
        }
      ],
      bottomMenus: [
        {
          icon: 'mdi-application',
          title: 'App',
          to: '/'
        }
      ]
    }
  }
}
</script>
