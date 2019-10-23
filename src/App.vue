<template>
  <v-app>
    <v-container fill height>
      <v-row justify="center" align="center">
        <v-col cols="12" class="text-center">
          <h1 class="display-4">Elizabeth Olvera's Portfolio</h1>
        </v-col>
        <v-col cols="12" class="text-center display-1">
          <p>eolver15@stu.southtexascollege.edu</p>
        </v-col>
        <v-col cols="12">
          <v-container>
            <v-row justify ="center">
              <v-col v-for="(project, index) in project" :key="index">
                <v-card max-width="344" class="mx-auto">
                  <v-list-item>
                    <v-list-item-content>
                      <v-list-item-title class="headline">{{project.name}}</v-list-item-title>
                    
                    </v-list-item-content>
                  </v-list-item>

                  <v-img :src="project.screenshot" contain height="194"></v-img>

                  <v-card-text>{{project.description}}</v-card-text>

                  <v-card-actions>
                    <v-btn text color="blue accent-4" :href="project.url" target="_blank">Go to site</v-btn> 
                    <div class="flex-grow-1"></div>
                    <v-btn icon>
                      <v-icon>mdi-share-variant</v-icon>
                    </v-btn>
                  </v-card-actions>
                </v-card>
              </v-col>
            </v-row>
          </v-container>
        </v-col>
      </v-row>
    </v-container>
  </v-app>
</template>

<script>
export default {
  name: "App",
  data: () => ({
    project : [
      {
        name: 'Vue Todo Application',
        description:'A simple to do application who handles completed and pending tasks, it also keeps records of total tasks per bucket.',
        screenshot:'/images/Vacation Packing List.jpg',
        url: 'https://todo.eolver15.site',
      },
        {
        name: 'Marvel Finder',
        description:'Using Marvel Public API, we have a simple character finder application, with character descriptions and some comics where the characters appear.',
        screenshot:'/images/Marvel Finder.jpg',
        url:'https://marvelfinder.eolver15.site',
      },
       {
        name: 'Super Awesome App',
        description:'The coolest and better Social Network ever created (by me).',
        screenshot:'/images/superawesomeapp.jpg',
        url: 'https://superawesomeapp.eolver15.site',
      },
      {
        name: 'Piano Me',
        description:'This is a simple piano lesson site. Students will learn online at their own pace.',
        screenshot:'/images/pmeapp.jpg',
        url: 'https://pianome.eolver15.site',
      }
    ]
  }),
  methods:{
    async share (project) {
      if (navigator.share){
        await navigator.share({
          title: project.any, 
          text: project.description,
          url: project.url
        })
      }
    }
  }
};
</script>
