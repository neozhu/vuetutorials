<template>
  <v-app>
    <v-toolbar app>
      <v-toolbar-title class="headline text-uppercase">
        <span>m-Show </span>
        <span class="font-weight-light"> MATERIAL DESIGN</span>
      </v-toolbar-title>
      <v-spacer></v-spacer>
      
    </v-toolbar>

    <v-content>
     <router-view></router-view>
    </v-content>
  </v-app>
</template>

<script>
import mapview from './components/map-view'

export default {
  name: 'App',
  components: {
    mapview
  },
  data () {
    return {
      //
    }
  }
}
</script>
