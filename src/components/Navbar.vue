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
          <p class="white--text subheading mt-1">Bobby Pratama</p>
        </v-flex>
        <v-flex class="mt-4 mb-3">
          <Popup />
        </v-flex>
      </v-layout>
      <v-list>
        <v-list-tile v-for="link in links" :key="link.text" router :to="link.route">
          <v-list-tile-action>
            <v-icon class="white--text">{{link.icon}}</v-icon>
          </v-list-tile-action>
          <v-list-tile-content>
            <v-list-tile-title class="white--text">{{link.text}}</v-list-tile-title>
          </v-list-tile-content>
        </v-list-tile>
      </v-list>
    </v-navigation-drawer>
  </nav>
</template>

<script>
import Popup from "./Popup.vue";
export default {
  components: {
    Popup
  },
  data() {
    return {
      drawer: false,
      links: [
        {
          icon: "dashboard",
          text: "All",
          route: "/"
        },
        {
          icon: "folder",
          text: "Teh",
          route: "/projects"
        },
        {
          icon: "person",
          text: "Kopi",
          route: "/team"
        }
      ]
    };
  }
};
</script>