<template>
  <v-app>
    <v-toolbar app>
      <v-toolbar-title  class="headline text-uppercase">
        <span>m-Show </span>
        <span class="font-weight-light"> MATERIAL DESIGN</span>
      </v-toolbar-title>
      <v-spacer></v-spacer>
      <v-toolbar-items >
           <v-btn to="/" color="primary" flat icon  >
              <v-icon>home</v-icon>
            </v-btn>
   
      
    </v-toolbar-items>
    </v-toolbar>

    <v-content>
     <router-view></router-view>
    </v-content>
  </v-app>
</template>

<script>


export default {
  name: 'App',
  data () {
    return {
      //
    }
  }
}
</script>
