<template>
  <v-app>
    <v-app-bar
      app
      color="primary"
      dark
    >
      <v-toolbar-title>パラノイア キャラクターシート作成ツール</v-toolbar-title>
    </v-app-bar>

    <v-main>
      <HelloWorld />
    </v-main>
  </v-app>
</template>

<script>
import HelloWorld from "./components/HelloWorld.vue";

export default {
  name: 'App',

  components: {
    HelloWorld
  },

  data: () => ({
    //
  }),
};
</script>
