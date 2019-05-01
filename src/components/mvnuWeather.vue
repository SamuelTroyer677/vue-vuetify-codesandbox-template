<template>
  <v-container>
    <v-layout align-center justify-center>
    <v-flex xs10>
    <v-card>
      <iframe id="forecast_embed" :frameborder="this.border" :height="this.height" :width="this.width" src='//forecast.io/embed/#lat=40.3934&lon=-82.4857&name=MVNU'></iframe>
    </v-card>
    </v-flex>
    </v-layout>
  </v-container>
</template>

<script>
export default {
  data: () => ({}),
  props: {
    height: String,
    width: String,
    border: String,
  },
  mounted: function() {;
  }
};
</script>

<style>
</style>

