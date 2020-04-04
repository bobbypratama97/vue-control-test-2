<template>
  <div class="team">
    <v-container class="my-5">
      <div>
        <v-dialog max-width="600px">
          <v-btn flat slot="activator" class="success">Show Cart</v-btn>
          <v-card class="text-xs-center">
            <v-card-title>Cart List</v-card-title>
            <v-card-text>
              <ul id="example-1">
                <li v-for="c in cart" :key="c">
                  {{ c.name }} - {{c.price}}
                  <span>
                    <v-btn small @click="addItem()">+</v-btn>
                    <v-btn small @click="removeItem()">-</v-btn>
                  </span>
                </li>
                <span>Total : {{this.total}}</span>
              </ul>
            </v-card-text>
          </v-card>
        </v-dialog>
        <v-btn
          v-for="(entry, index) in filterList"
          :item="entry"
          :key="index"
          @click="
          filter = entry;
          active = index;
        "
          :class="{ active: entry == filter }"
        >{{ entry }}</v-btn>
      </div>
      <v-layout row wrap>
        <v-flex
          xs12
          sm6
          md4
          lg3
          v-for="(entry,id) in products"
          v-if="resultsFilter(entry, 'mainProduct', filter)"
          :item="entry"
          :key="id"
          class="product"
        >
          <v-card flat class="text-xs-center ma-3 justify-center">
            <v-responsive class="pt-4">
              <v-avatar size="100" class="grey lighten-2">
                <img :src="entry.image" />
              </v-avatar>
            </v-responsive>
            <v-card-text>
              <div class="subheading font-weight-bold">{{entry.name}}</div>
              <div class="subheading font-weight-bold">{{entry.price}}</div>
              <div class="subheading font-weight-light">{{entry.description}}</div>
              <div class="grey--text">{{entry.category}}</div>
            </v-card-text>
            <v-card-actions>
              <v-flex class="text-center">
                <v-btn flat color="grey" @click="addItem(entry)">
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
      filterList: ["All", "Food", "Tea", "Coffee"],
      filter: "All",
      products: [],
      cart: [],
      user: [],
      total: 0,
      productFilterKey: "all"
    };
  },
  computed: {},
  created() {
    axios
      .get("http://localhost:3000/user")
      .then(response => (this.user = response.data));

    axios
      .get("http://localhost:3000/products")
      .then(response => (this.products = response.data));
  },
  methods: {
    resultsFilter(entry) {
      if (this.filter !== "All") {
        if (entry.category === this.filter) {
          return entry;
        }
      } else {
        return entry;
      }
    },
    addItem(p) {
      var i,
        cek = 0;
      for (i = 0; i < this.cart.length; i++) {
        if (this.cart[i].name === p.name) {
          this.cart[i].price = this.cart[i].price + p.price;
          this.total = this.total + p.price;
          cek = 1;
        }
      }
      if (cek != 1) {
        this.cart.push(p);
        this.total = this.total + p.price;
        // console.log(this.cart);
      }
    }
  }
};
</script>
