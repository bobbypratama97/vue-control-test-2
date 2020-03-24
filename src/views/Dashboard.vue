<template>
  <div class="team">
    <v-container class="my-5">
      <v-layout row wrap>
        <v-flex xs12 sm6 md4 lg3 v-for="person in team" :key="person.name">
          <v-card flat class="text-xs-center ma-3">
            <v-responsive class="pt-4">
              <v-avatar size="100" class="grey lighten-2">
                <img :src="person.avatar" />
              </v-avatar>
            </v-responsive>
            <v-card-text>
              <div class="subheading">{{person.name}}</div>
              <div class="grey--text">{{person.role}}</div>
            </v-card-text>
            <v-card-actions>
              <v-btn flat color="grey">
                <v-icon small left>message</v-icon>
                <v-btn @click="showTeam">A</v-btn>
                <span>Message</span>
              </v-btn>
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
      team2: [],
      team: [
        {
          name: "Bobby Pratama",
          role: "Chief Marketing Officer",
          avatar: "/ronaldo.jpg"
        },
        {
          name: "Ian Yulistio Susilo",
          role: "Chief Technology Officer",
          avatar: "/ronaldo.jpg"
        },
        {
          name: "Verryanto Paulus",
          role: "Head of Software",
          avatar: "/ronaldo.jpg"
        },
        {
          name: "Komang Arinanda",
          role: "Chief Executive Organizer",
          avatar: "/ronaldo.jpg"
        },
        {
          name: "Adrian Hartanto",
          role: "Head of Architecture Team",
          avatar: "/ronaldo.jpg"
        }
      ]
    };
  },
  methods: {
    created() {
      axios
        .get("http://localhost:3000/user")
        .then(response => (this.team2 = response))
        .catch(error => console.log(error));
      console.log(this.team2);
    },
    showTeam() {
      console.log("test");
      // console.log(this.team2);
    }
  }
};
</script>
