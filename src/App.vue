<template>
  <v-app>
    <v-toolbar>
      <v-img fluid max-height="50" max-width="50" v-bind:src="'https://pbs.twimg.com/profile_images/463038072846688256/NDuIYRqn.jpeg'"></v-img>       
      <v-toolbar-title class="display-1 font-weight-light">MVNU Cafe Menu</v-toolbar-title>
        </v-toolbar>
    <v-container>
      <!-- <cafeTitle v-bind:pic="'https://pbs.twimg.com/profile_images/463038072846688256/NDuIYRqn.jpeg'" /> -->
      <tweetMenu
        v-for="tweet in timeline"
        v-bind:key="tweet.id"
        v-bind:text="tweet.full_text"
        v-bind:tweetDate="tweet.created_at.substring(0, tweet.created_at.indexOf('+'))"
      ></tweetMenu>
    </v-container>
  </v-app>
</template>

<script>
import tweetMenu from "./components/tweetMenu";
import cafeTitle from "./components/cafeTitle";
export default {
  name: "App",
  components: {
    tweetMenu,
    cafeTitle
  },

  data() {
    return {
      timeline: []
    };
  },
  mounted: async function() {
    let response = await fetch(
      "http://98.27.202.77/mvnu/testingFinal/test.php",
      { mode: "cors" }
    );
    this.timeline = await response.json();
    console.log(this.timeline);
  }
};
</script>

<style>
</style>
