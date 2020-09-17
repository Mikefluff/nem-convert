<template>
  <v-app>
    <v-app-bar
      app
      color="primary"
      dark
    >
      <div class="d-flex align-center">
         <span class="mr-1">Nem key convertor</span>
      </div>

      <v-spacer></v-spacer>

      <v-btn
        href="https://chrono.tech"
        target="_blank"
        text
      >
        <span class="mr-2">Chrono tech</span>
        <v-icon>mdi-open-in-new</v-icon>
      </v-btn>
    </v-app-bar>

    <v-content>
      <Converter/>
    </v-content>
  </v-app>
</template>

<script>
import Converter from './components/Converter';

export default {
  name: 'App',

  components: {
    Converter,
  },

  data: () => ({
    //
  }),
};
</script>
