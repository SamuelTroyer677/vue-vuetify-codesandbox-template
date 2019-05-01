<template>
  <v-app>
    <v-toolbar>
      <v-img
        fluid
        max-height="50"
        max-width="50"
        v-bind:src="'https://pbs.twimg.com/profile_images/463038072846688256/NDuIYRqn.jpeg'"
      ></v-img>
      <v-toolbar-title class="display-1 font-weight-light">MVNU Cafe Menu</v-toolbar-title>
      <v-spacer></v-spacer>
    <v-toolbar-items class="hidden-sm-and-down">
      <i title="MVNU Cafe Twitter" onclick="window.location = 'https://twitter.com/MVNUDining'" class="material-icons linkIcon">link</i>
    </v-toolbar-items>
    </v-toolbar>
    <mvnuWeather v-bind:height="'220'" v-bind:width="'100%'" v-bind:border="'0'" />
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
import mvnuWeather from "./components/mvnuWeather";
export default {
  name: "App",
  components: {
    tweetMenu,
    mvnuWeather,
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
.linkIcon {
  display: flex;
  justify-content: center;
  align-items: center;
  font-size: 40px;
  cursor: pointer;
}
</style>
