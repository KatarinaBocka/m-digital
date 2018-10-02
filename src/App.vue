<template>
  <v-app>
      <v-navigation-drawer fixed v-model="sideNav">
        <v-list>
          <v-list-tile>
          <v-list-tile-action>
            <i class="fas fa-home"></i>
          </v-list-tile-action>
          <v-list-tile-content>
            <v-list-tile-title>Home</v-list-tile-title>
          </v-list-tile-content>
        </v-list-tile>
        </v-list>
      </v-navigation-drawer>
      <v-toolbar color="primary" dark>
        <v-toolbar-side-icon class="hidden-sm-and-up" @click="sideNav = !sideNav"></v-toolbar-side-icon>
        <v-toolbar-title>Project Quote</v-toolbar-title>
        <v-spacer></v-spacer>
        <v-toolbar-items class="hidden-xs-only">
          <v-btn flat>Link 1</v-btn>
          <v-btn flat>Link 2</v-btn>
          <v-btn flat>Link 3</v-btn>
        </v-toolbar-items>
    </v-toolbar>
    <v-content>
      <HelloWorld/>
    </v-content>

  </v-app>
</template>

<script>
import HelloWorld from './components/HelloWorld'

export default {
  name: 'App',
  components: {
    HelloWorld
  },
  data () {
    return {
      sideNav: false,
      // clipped: false,
      // drawer: true,
      // fixed: false,
      // items: [{
      //   icon: 'fas fa-shapes',
      //   title: 'Inspire'
      // }],
      // miniVariant: false,
      // right: true,
      // rightDrawer: false,
      // title: 'Vuetify.js'
    }
  }
}
</script>
