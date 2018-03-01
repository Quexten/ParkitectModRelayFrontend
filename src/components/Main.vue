<template>
      <v-container fluid fill-height>
        <v-layout align-center justify-center>
          <v-flex xs12 sm8 md4>
            <v-card class="elevation-12">
              <v-toolbar dark color="primary">
              <v-toolbar-title>Parkitect Mod Portal</v-toolbar-title>
                <v-spacer></v-spacer>
              </v-toolbar>
              <v-content>
                <v-card-text>
                  <v-text-field v-model="link" color="primary" label = "Workshop Link"></v-text-field>
                </v-card-text>
                <v-btn
                  color="accent"
                  :loading="downloading"
                  @click.native="download(link)"
                  :disabled="downloading"                >
                  Download
                </v-btn>
              </v-content>
            </v-card>
          </v-flex>
        </v-layout>
      </v-container>
</template>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h1, h2 {
  font-weight: normal;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>

<script>
  import axios from 'axios'

  export default {
    data () {
      return {
        link: '',
        downloading: false
      }
    },
    methods: {
      download: function (workshoplink) {
        var self = this
        self.downloading = true

        var itemId = workshoplink.match(/\d+$/)
        axios.get('parkitect-api-marnit.dynv6.net', {
          item_id: itemId
        })
        .then(function (response) {
          window.location.href = response.data.download
          self.downloading = false
        })
        .catch(function (error) {
          self.error = error
          self.downloading = false
        })
      }
    }
  }
</script>
