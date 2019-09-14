<template>
  <v-app-bar app>
    <v-btn>
      <v-icon>far fa-lightbulb</v-icon>
    </v-btn>
    <v-spacer></v-spacer>
    <v-toolbar-title class="headline text-uppercase">
        <router-link to="/">
          <img src="https://motionwall.it/images/logo.png?2f57c55fef63e7b9bb8082dc21c5541e" alt="Motionwall logo">
        </router-link>
    </v-toolbar-title>
    <v-spacer></v-spacer>
    <v-btn
      text
      href="https://www.instagram.com/motionwallit/"
      target="_blank"
    >
      <v-icon>fab fa-instagram</v-icon>
    </v-btn>
  </v-app-bar>
</template>

<script>
export default {

}
</script>

<style scoped>
  img {
    width: 40px;
  }
</style>