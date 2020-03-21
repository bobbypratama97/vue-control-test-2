<template>
  <div class="team">
    <h1 class="subheading grey--text">Meet Our Team</h1>
    <v-container class="my-5">
      <v-layout row wrap>
        <v-flex xs12 sm6 md4 lg3 v-for="person in team" :key="person.name">
          <v-card flat class="text-xs-center ma-3">
            <v-responsive class="pt-4">
              <v-avatar size="100" class="grey lighten-2">
                <img :src="person.avatar">
              </v-avatar>
            </v-responsive>
            <v-card-text>
              <div class="subheading">{{person.name}}</div>
              <div class="grey--text">{{person.role}}</div>
            </v-card-text>
            <v-card-actions>
              <v-btn flat color="grey">
                <v-icon small left>message</v-icon>
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
export default {
  data() {
    return {
      team: [
        {
          name: "Bobby Pratama",
          role: "Chief Marketing Officer",
          avatar: "/ronaldo.jpg"
        },
        {
          name: "Ian Yulistio Susilo",
          role: "Chief Technology Officer",
          avatar: "/reus.jpg"
        },
        {
          name: "Verryanto Paulus",
          role: "Head of Software",
          avatar: "/messi.jpg"
        },
        {
          name: "Komang Arinanda",
          role: "Chief Executive Organizer",
          avatar: "/kroos.jpg"
        },
        {
          name: "Adrian Hartanto",
          role: "Head of Architecture Team",
          avatar: "/kaka.jpg"
        }
      ]
    };
  }
};
</script>
