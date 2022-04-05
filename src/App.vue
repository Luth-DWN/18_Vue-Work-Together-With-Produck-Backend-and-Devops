<template>


  <v-app light>

  <SideMenu :drawer="drawer"  :api_key="api_key" @selectsource="setResource" ></SideMenu>

  <v-toolbar fixed app light clipped-left color="primary">
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
import SideMenu from './components/SideMenu.vue'
import MainContent from './components/MainContent.vue'


export default {

  components: {
      SideMenu,
      MainContent
  },

  data() {
    return {
      drawer: true,
      // api_key:'9e704ef41bb048afb46a851b69d62a28',
      articles: [],
      errors: [] 
    }
  },


  created () {
    axios.get('https://newsapi.org/v2/top-headlines?sources=techcrunch&apiKey=9e704ef41bb048afb46a851b69d62a28')
      .then(response => {
        this.articles = response.data.articles
        console.log('data:')
        console.log(response.data.articles)
      .catch(e => {
        this.errors.push(e)
      })
    })
  },


  methods: {
     
      setResource(source){

        axios.get('https://newsapi.org/v2/top-headlines?sources='+source+'&apiKey=9e704ef41bb048afb46a851b69d62a28')
        .then(response => {
          this.articles = response.data.articles
          console.log('Source Articles:')
          console.log(response.data.articles)
        })
        .catch(e => {
          this.errors.push(e)
        })

      }
   }

  }
</script>