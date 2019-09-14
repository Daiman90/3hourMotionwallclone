<template>
  <div class="flex xa12 smd4 lg3">
    <div class="align-items-center hidden-lg-and-up">
      <v-list light>
        <v-list-item>
          <v-list-item-avatar>
            <v-img
              :src="profUrl"
            >
              
            </v-img>
          </v-list-item-avatar>
          <v-list-item-content left>
            <v-list-item-title>{{result.name}}</v-list-item-title>
            <v-list-item-subtitle>{{result.title}}</v-list-item-subtitle>
          </v-list-item-content>
          <v-list-item-action>
            <v-icon>mdi-dots-horizontal</v-icon>
          </v-list-item-action>
        </v-list-item>
      </v-list>
    </div>
    <v-card>
      <router-link :to="{name: 'document', params:  { id: result.document.toString()}}">
        <v-img class="image-feed"
        :src="result.mediumUrl"
        >

        </v-img>
      </router-link>
      <v-card-text>
        {{result.description}}
      </v-card-text>
    </v-card>
  </div>
</template>

<script>
export default {
  props: {
    result: Object,
  },
  computed: {
    profUrl: function() {
      return `https://motionwall.it${this.result.profileImage}`;
    }
  }
}
</script>

<style>
.image-feed {
  border-radius: 20px!important;
}

</style>