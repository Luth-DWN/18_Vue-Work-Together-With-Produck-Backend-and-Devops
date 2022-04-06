<template>

  <v-layout row wrap align-center>
    <v-navigation-drawer
      absolute
      permanent
      left
    >

      <v-list dense>
        <v-list-item
          v-for="article in articles"
          :key="article.id"
        >
          <v-list-item-avatar>
            <img src="https://randomuser.me/api/portraits/lego/1.jpg">
          </v-list-item-avatar>

          <v-list-item-content>
            <v-list-item-title>{{ article.name }}</v-list-item-title>
          </v-list-item-content>
        </v-list-item>
      </v-list>
    </v-navigation-drawer>
    
    <v-flex xs8 offset-md2>
      <div v-for="article in articles" :key="article.id">
        <v-card class="my-3" hover>
          <v-img height="350px" v-bind:src="article.image_link"></v-img>
          <v-container fill-height fluid>
            <v-layout>
              <v-flex xs12 align-end d-flex>
                <span class="headline">{{ article.title }}</span>
              </v-flex>
            </v-layout>
          </v-container>
          <v-card-text  class="black--text text-darken-1 mb-2 font-weight-bold">
            {{ article.name }}
          </v-card-text>
          <v-card-text>
            {{ article.description }}
          </v-card-text>
          <v-card-actions>
            <v-chip small color="secondary" class="white--text">
              {{ article.brand }}
            </v-chip>
            <v-spacer></v-spacer>
            <v-btn icon class="red--text">
              <v-icon small>fa-reddit</v-icon>
            </v-btn>
            <v-btn icon class="light-blue--text">
              <v-icon small>fa-twitter</v-icon>
            </v-btn>
            <v-btn icon class="blue--text text--darken-4">
              <v-icon small>fa-facebook</v-icon>
            </v-btn>
            <v-btn icon class="red--text">
              <v-icon small>fa-google-plus</v-icon>
            </v-btn>
            <v-btn icon class="blue--text text--darken-4">
              <v-icon small>fa-linkedin</v-icon>
            </v-btn>
            <v-spacer></v-spacer>

            <v-btn
              small
              replace
              color="info"
              v-bind:href="article.product_api_url"
              target="_blank"
              >Read More</v-btn
            >
          </v-card-actions>
        </v-card>
      </div>
    </v-flex>
  </v-layout>
</template>

<script>
export default {
  props: {
    articles: Array,
  },
};
</script>

<style>
.text-darken-1 mb-2 font-weight-bold{
 font-size: 3em;
}
</style>