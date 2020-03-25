<template>
  <nav>
    <v-toolbar flat app>
      <v-toolbar-side-icon class="grey--text" @click="drawer = !drawer"></v-toolbar-side-icon>
      <v-toolbar-title class="text-uppercase grey--text">
        <span class="font-weight-light">BOBBY</span>
        <span>CAFE</span>
      </v-toolbar-title>
      <v-spacer></v-spacer>

      <v-btn flat color="grey">
        <span>Sign Out</span>
        <v-icon right>exit_to_app</v-icon>
      </v-btn>
    </v-toolbar>

    <v-navigation-drawer app v-model="drawer" class="primary">
      <v-layout column align-center>
        <v-flex class="mt-5">
          <v-avatar size="100">
            <img src="/ronaldo.jpg" />
          </v-avatar>
          <p class="white--text subheading mt-1">{{user[0].name}}</p>
        </v-flex>
        <v-flex class="mt-4 mb-3">
          <Popup />
        </v-flex>
      </v-layout>
    </v-navigation-drawer>
  </nav>
</template>

<script>
import axios from "axios";
import Popup from "./Popup.vue";
export default {
  components: {
    Popup
  },
  data() {
    return {
      user: [],
      drawer: false
    };
  },
  mounted() {
    axios
      .get("http://localhost:3000/user")
      .then(response => (this.user = response.data));
  }
};
</script>