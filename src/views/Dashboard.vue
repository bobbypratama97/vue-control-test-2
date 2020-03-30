<template>
  <div class="team">
    <v-container class="my-5">
      <v-layout row class="mb-3">
        <v-tooltip top>
          <v-btn small flat color="grey" @click="sortBy('title')" slot="activator">
            <v-icon left small>folder</v-icon>
            <span class="caption text-lowercase">Show Cart</span>
          </v-btn>
          <span>Show Cart</span>
        </v-tooltip>
        <v-btn
          small
          flat
          color="grey"
          v-for="(entry, index) in filterList"
          :item="entry"
          :key="index"
          @click="
          filter = entry;
          active = index;
        "
          :class="{ active: entry == filter }"
        >
          <v-icon left small>fastfood</v-icon>
          {{ entry }}
        </v-btn>
      </v-layout>
      <v-layout row wrap>
        <v-flex
          xs12
          sm6
          md4
          lg3
          v-for="(product,id) in products"
          :item="product"
          :key="id"
          class="product"
        >
          <v-card flat class="text-xs-center ma-3 justify-center">
            <v-responsive class="pt-4">
              <v-avatar size="100" class="grey lighten-2">
                <img :src="product.image" />
              </v-avatar>
            </v-responsive>
            <v-card-text>
              <div class="subheading font-weight-bold">{{product.name}}</div>
              <div class="subheading font-weight-bold">{{product.price}}</div>
              <div class="subheading font-weight-light">{{product.description}}</div>
              <div class="grey--text">{{product.category}}</div>
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
  data: function() {
    return {
      fkey: "mainProduct",
      filterList: ["Food", "Tea", "Coffee"],
      filter: "All",
      products: [],
      cart: [],
      user: [],
      productFilterKey: "all"
    };
  },
  computed: {
    // productFilter() {
    //   return this[this.productFilterKey];
    // },
    // all() {
    //   return this.products;
    // },
    // food() {
    //   return this.products.filter(product => product.category == "Food");
    // }
    // filteredFood() {
    //   return this.products.filter(product => {
    //     return product.category.match("Food");
    //   });
    // }
  },
  created() {
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
    }
  }
};
</script>
