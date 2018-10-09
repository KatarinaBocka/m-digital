<template>
  <v-app>
    <Header/>
    <v-content>
      <Request/>
    </v-content>

  </v-app>
</template>

<script>
import Request from './components/Request'
import Header from './components/Header'

export default {
  name: 'App',
  components: {
    Request,
    Header
  },
  // data () {
  //   return {
  //     sideNav: false,
  //   }
  // }
}
</script>
<style scoped>
#app {
  background-image: url("../src/assets/gray.jpg")
}
</style>