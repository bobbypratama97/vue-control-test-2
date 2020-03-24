<template>
  <div class="team">
    <v-container class="my-5">
      <v-layout row wrap>
        <v-flex xs12 sm6 md4 lg3 v-for="p in products" :key="p.id">
          <v-card flat class="text-xs-center ma-3 justify-center">
            <v-responsive class="pt-4">
              <v-avatar size="100" class="grey lighten-2">
                <img :src="p.image" />
              </v-avatar>
            </v-responsive>
            <v-card-text>
              <div class="subheading font-weight-bold">{{p.name}}</div>
              <div class="subheading font-weight-bold">{{p.price}}</div>
              <div class="subheading font-weight-light">{{p.description}}</div>
              <div class="grey--text">{{p.category}}</div>
            </v-card-text>
            <v-card-actions>
              <v-flex class="text-center">
                <v-btn flat color="grey">
                  <span>Add to Cart</span>
                </v-btn>
              </v-flex>
            </v-card-actions>
          </v-card>
        </v-flex>
      </v-layout>
    </v-container>
  </div>
</template>

<script>
import axios from "axios";
export default {
  data() {
    return {
      user: [],
      products: []
    };
  },
  mounted() {
    axios
      .get("http://localhost:3000/user")
      .then(response => (this.user = response.data));

    axios
      .get("http://localhost:3000/products")
      .then(response => (this.products = response.data));
  }

  // showTeam() {
  //   console.log(this.team2);
  //   // console.log(this.team2);
  // }
  // }
};
</script>
