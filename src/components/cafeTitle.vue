<template>
  <v-container>
        <v-toolbar>
        <v-img fluid max-height="150" max-width="150" v-bind:src="pic"></v-img>
      <span class="display-4 font-weight-light">MVNU Cafe Menu</span>
        </v-toolbar>
  </v-container>
</template>

<script>
export default {
  data: () => ({}),
  props: {
      pic: String
  }
};
</script>

<style>
.picture {
  max-width: 150px;
  max-height: 150px;
}
</style>

