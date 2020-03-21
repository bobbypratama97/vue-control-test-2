<template>
  <div class="dashboard">
    <h1 class="subheading grey--text">Dashboard</h1>
    <v-container class="my-5">
      <v-layout row class="mb-3">
        <v-tooltip top>
          <v-btn small flat color="grey" @click="sortBy('title')" slot="activator">
            <v-icon left small>fastfood</v-icon>
            <span class="caption text-lowercase">Teh</span>
          </v-btn>
          <span>Sort Card by Category</span>
        </v-tooltip>
        <v-tooltip top>
          <v-btn small flat color="grey" @click="sortBy('title')" slot="activator">
            <v-icon left small>fastfood</v-icon>
            <span class="caption text-lowercase">Kopi</span>
          </v-btn>
          <span>Sort Card by Project Category</span>
        </v-tooltip>
        <v-tooltip top>
          <v-btn small flat color="grey" @click="sortBy('title')" slot="activator">
            <v-icon left small>fastfood</v-icon>
            <span class="caption text-lowercase">Makanan</span>
          </v-btn>
          <span>Sort Card by Category</span>
        </v-tooltip>
      </v-layout>
      <v-card flat v-for="project in projects" :key="project.title">
        <h1>Test</h1>
      </v-card>
    </v-container>
  </div>
</template>

<script>
export default {
  data() {
    return {
      projects: [
        {
          title: "Design SITF on Adobe XD",
          person: "Bobby",
          due: "8 February 2019",
          status: "Ongoing",
          content: "Test"
        },
        {
          title: "Code Up The Homepage",
          person: "Verry",
          due: "15 February 2019",
          status: "Complete",
          content: "Test"
        },
        {
          title: "Design Video Thumbnails",
          person: "Ian",
          due: "10 February 2019",
          status: "Overdue",
          content: "Test"
        },
        {
          title: "Create A Community Forum",
          person: "Komang",
          due: "28 February 2019",
          status: "Overdue",
          content: "Test"
        }
      ]
    };
  },
  methods: {
    sortBy(prop) {
      this.projects.sort((a, b) => (a[prop] < b[prop] ? -1 : 1));
    }
  }
};
</script>

<style>
.project.Complete {
  border-left: 4px solid #3cd1c2;
}
.project.Ongoing {
  border-left: 4px solid orange;
}
.project.Overdue {
  border-left: 4px solid tomato;
}

.v-chip.Complete {
  background: #3cd1c2;
}

.v-chip.Ongoing {
  background: #ffaa2c;
}

.v-chip.Overdue {
  background: #f83e70;
}
</style>