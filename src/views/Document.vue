<template>
<v-content>
    <div class="flex xs12 sm8">
      <div class="container">
          <v-list light>
            <v-list-item>
              <v-list-item-avatar>
                <v-img
                  :src="profUrl"
                >       
                </v-img>
              </v-list-item-avatar>
              <v-list-item-content left>
                <v-list-item-title>{{data.name}}</v-list-item-title>
              </v-list-item-content>
            </v-list-item>
          </v-list>
        </div>
        <div class="layout row">
          <div class="flex xs12 lg8">
            <v-window>
              <v-window-item class="mx-auto slide-images rouded-image">
                <v-img :src="data.url"></v-img>
              </v-window-item>
            </v-window>
          </div>
        </div>
        <div class="flex text-left xs12 sm4">
          <div class="container">
            <span class="feed-subtitle d-flex mt-5">
              {{data.title}}
            </span>
            <span class="subtitle-1">
              {{data.description}}
            </span>
            <v-btn>
              <svg aria-hidden="true" focusable="false" data-prefix="far" data-icon="arrow-alt-circle-down" role="img" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 512 512" class="mr-2 svg-inline--fa fa-arrow-alt-circle-down fa-w-16"><path fill="currentColor" d="M256 8C119 8 8 119 8 256s111 248 248 248 248-111 248-248S393 8 256 8zm0 448c-110.5 0-200-89.5-200-200S145.5 56 256 56s200 89.5 200 200-89.5 200-200 200zm-32-316v116h-67c-10.7 0-16 12.9-8.5 20.5l99 99c4.7 4.7 12.3 4.7 17 0l99-99c7.6-7.6 2.2-20.5-8.5-20.5h-67V140c0-6.6-5.4-12-12-12h-40c-6.6 0-12 5.4-12 12z" class=""></path></svg>
              <span>Download</span>
            </v-btn>
          </div>
        </div>
  </div>

</v-content>
</template>

<script>
export default {
  data: () => ({
    data: [],
  }),
  mounted() {
    this.getData();
  },
  computed: {
    profUrl: function() {
      return `https://motionwall.it${this.data.profile_image}`;
    }
  },
  methods: {
    async getData() {
      const response = await fetch('https://cors-anywhere.herokuapp.com/https://motionwall.it/api/imagedetail/281');
      const result = await response.json();
      this.data = await result[0]
    }
  }
}
</script>

<style>

</style>