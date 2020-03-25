<template>
  <v-dialog max-width="600px">
    <v-btn flat slot="activator" class="success">Show Cart</v-btn>
    <div class="text-xs-center">
      <v-card>
        <h1>Cart</h1>
        <v-card-text></v-card-text>
        <v-card-actions class="justify-center">
          <v-btn>Checkout</v-btn>
        </v-card-actions>
      </v-card>
    </div>
  </v-dialog>
</template>

<script>
import format from "date-fns/format";
export default {
  data() {
    return {
      title: "",
      content: "",
      categoryList: ["Tea", "Coffee", "Food"],
      due: null,
      inputRules: [v => v.length >= 3 || "Minimum length is 3 character"]
    };
  },
  methods: {
    submit() {
      if (this.$refs.form.validate()) {
        console.log(this.title, this.content);
      }
    }
  },
  computed: {
    formattedDate() {
      return this.due ? format(this.due, "Do MMM YYYY") : "";
    }
  }
};
</script>