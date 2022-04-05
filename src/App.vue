<template>
<v-app light>
  <v-toolbar fixed app light clipped-left color="primary" class="elevation-2">
    <v-toolbar-side-icon @click="drawer = !drawer"  class="white--text"></v-toolbar-side-icon>
    <v-toolbar-title class="white--text">News App</v-toolbar-title>
  </v-toolbar>

  <v-content>
    <v-container fluid>
      <MainContent :articles="articles"></MainContent> 
    </v-container>
   </v-content>
  </v-app>


</template>

<script>

import axios from 'axios'
import MainContent from './components/MainContent.vue'

export default {

  components: {
        MainContent,
  },

  data() {
    return {
      drawer: false,
      api_key:'9e704ef41bb048afb46a851b69d62a28',
      articles: [],
      errors: [] 
    }
  },
  created () {
    axios.get('https://newsapi.org/v2/top-headlines?sources=techcrunch&apiKey='+this.api_key)
      .then(response => {
        this.articles = response.data.articles
        console.log('data:')
        console.log(response.data.articles)
      })
      .catch(e => {
        this.errors.push(e)
      })
  },


  }
</script>