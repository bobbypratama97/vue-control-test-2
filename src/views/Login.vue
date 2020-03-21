  
<template>
  <v-app id="inspire">
    <v-content>
      <v-container class="fill-height" fluid>
        <v-row align="center" justify="center">
          <v-col cols="12" sm="8" md="4">
            <v-card class="elevation-12">
              <v-toolbar color="primary" dark flat>
                <v-toolbar-title>Bobby's Cafe</v-toolbar-title>
                <v-spacer />
              </v-toolbar>
              <v-card-text>
                <v-form ref="form" lazy-validation>
                  <v-text-field label="Username" name="login" type="text" v-model="username" />
                  <v-text-field
                    id="password"
                    label="Password"
                    name="password"
                    type="password"
                    v-model="password"
                  />
                </v-form>
                <v-btn color="primary" @click="login()">Login</v-btn>
              </v-card-text>
            </v-card>
          </v-col>
        </v-row>
      </v-container>
    </v-content>
  </v-app>
</template>

<script>
import axios from "axios";
export default {
  data() {
    return {
      master: [],
      username: "",
      password: ""
    };
  },
  methods: {
    login: function() {
      var username = "",
        password = "";
      axios
        .get("http://localhost:3000/user")
        .then(response => (this.master = response.data[0]))
        .catch(error => console.log(error));
      // console.log(this.master);
      username = this.master.username;
      password = this.master.password;
    }
  }
};
</script>