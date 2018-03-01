<template>
  <v-app>
    <v-content>
      <router-view/>
    </v-content>
    <v-footer :fixed="fixed" app>
      <span>Code by</span>
      <v-btn flat color="primary" @click.native="visitQuexten()">Quexten</v-btn>
      <span>Hosting and PR by</span>
      <v-btn flat color="primary" @click.native="visitMarnit()">Marnit</v-btn>
      <v-spacer></v-spacer>
      <span>With 💖 on</span>
      <v-btn flat color="primary" @click.native="visitGithub()">GitHub</v-btn>
    </v-footer>
  </v-app>
</template>

<script>
export default {
  methods: {
    visitMarnit: function () {
      window.location.href = 'https://github.com/themarnit'
    },
    visitQuexten: function () {
      window.location.href = 'https://github.com/quexten'
    },
    visitGithub: function () {
      window.location.href = 'https://github.com/parkitectattac/'
    }
  }
}
</script>

