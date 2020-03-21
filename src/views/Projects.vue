<template>
  <div class="projects">
    <h1 class="subheading grey--text">Projects</h1>
    <v-container class="my-5">
      <v-expansion-panel>
        <v-expansion-panel-content v-for="project in myProjects" :key="project.title">
          <div slot="header">{{project.title}}</div>
          <v-card>
            <v-card-text class="px-4 grey--text">
              <div class="font-weight-bold">{{project.due}}</div>
              <div>{{project.content}}</div>
            </v-card-text>
          </v-card>
        </v-expansion-panel-content>
      </v-expansion-panel>
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
  computed: {
    myProjects() {
      return this.projects.filter(project => {
        return project.person == "Bobby";
      });
    }
  }
};
</script>
