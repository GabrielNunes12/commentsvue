<template>
  <v-app>
    <v-app-bar
      app
      color="primary"
      dark
    >
      <div id="app">
      </div>

      <v-spacer></v-spacer>

      <v-btn
        href="https://github.com/vuetifyjs/vuetify/releases/latest"
        target="_blank"
        text
      >
        <span class="mr-2">Latest Release</span>
        <v-icon>mdi-open-in-new</v-icon>
      </v-btn>
    </v-app-bar>

    <v-main>
      <Comments/>
    </v-main>
  </v-app>
</template>

<script>
import Comments from './components/Comments';

export default {
  name: 'App',

  components: {
    Comments,
  },

  data: () => ({
    //
  }),
};
</script>
