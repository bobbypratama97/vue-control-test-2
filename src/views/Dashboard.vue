<template>
  <div class="team">
    <v-container class="my-5">
      <v-layout row class="mb-3">
        <v-dialog max-width="600px">
          <v-btn small flat color="grey" @click="sortBy('title')" slot="activator">
            <v-icon left small>folder</v-icon>
            <span class="caption text-lowercase" @click="drawer = true">Show Cart</span>
          </v-btn>
          <div class="text-xs-center">
            <v-card>
              <h1>Cart</h1>
              <v-card-text>
                <ul id="example-1">
                  <li v-for="c in cart" :key="c.id">
                    {{ c.name }} - {{c.price}}
                    <!-- {{this.price = this.price+c.price}} -->
                  </li>
                </ul>
              </v-card-text>
              <v-card-actions class="justify-center">
                <v-btn @click="countPrice(cart)">Checkout</v-btn>
              </v-card-actions>
            </v-card>
          </div>
        </v-dialog>
        <v-tooltip top>
          <v-btn small flat color="grey" @click="sortBy('person')" slot="activator">
            <v-icon left small>dashboard</v-icon>
            <span class="caption text-lowercase">All</span>
          </v-btn>
          <span>Show all products</span>
        </v-tooltip>
        <v-tooltip top>
          <v-btn small flat color="grey" @click="sortBy('person')" slot="activator">
            <v-icon left small>fastfood</v-icon>
            <span class="caption text-lowercase">Food</span>
          </v-btn>
          <span>Show only Food</span>
        </v-tooltip>
        <v-tooltip top>
          <v-btn small flat color="grey" @click="sortBy('person')" slot="activator">
            <v-icon left small>emoji_food_beverage</v-icon>
            <span class="caption text-lowercase">Tea</span>
          </v-btn>
          <span>Show only Tea</span>
        </v-tooltip>
        <v-tooltip top>
          <v-btn small flat color="grey" @click="sortBy('person')" slot="activator">
            <v-icon left small>emoji_food_beverage</v-icon>
            <span class="caption text-lowercase">Coffee</span>
          </v-btn>
          <span>Show only Coffee</span>
        </v-tooltip>
      </v-layout>
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
                <v-btn flat color="grey" @click="addItem(p)">
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
      totalPrice: 0,
      drawer: false,
      cart: [],
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
  },
  methods: {
    addItem(p) {
      this.cart.push(p);
      console.log(this.cart);
    },
    countPrice(cart) {}
  }
  // showTeam() {
  //   console.log(this.team2);
  //   // console.log(this.team2);
  // }
  // }
};
</script>
