<template>
  <v-app>
    <v-app-bar
      app
      color="white"
      light
    >
      <div id="title" class="d-flex align-center">
        <h3>ARIAS-LABS</h3>
      </div>

      <v-spacer></v-spacer>

    </v-app-bar>

    <v-content class='backgroundColor'>
      <TipCalc />
    </v-content>
  </v-app>
</template>

<script>
import TipCalc from "./components/TipCalc"

export default {
  name: 'App',

  components: {
    TipCalc,
  },

  data: () => ({
    //
  }),
};
</script>

<style lang="scss">

 #title {
   h3 {
     font-family: futura-pt-condensed, sans-serif;
   }

 } 

 .backgroundColor {
   background: #c06c84;
 }


</style>
