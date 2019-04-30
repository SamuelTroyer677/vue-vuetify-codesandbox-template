<template>
  <v-container>
    <v-layout align-center justify-center column>
    <v-flex xs2 sm6 md4>
    <v-card class="text-sm-left elevation-12">
      <table class="menuTable">
        <tr>
          <th class="blue lighten-3 text-xs-center">
            {{tweetDate}}
          </th>
        </tr>
        <tr v-for="item in menuArray" :key="item">
          <td>{{item}}</td>
        </tr>
      </table> 
    </v-card>
    </v-flex>
    </v-layout>
  </v-container>
</template>

<script>
export default {
  name: "tweetMenu",
 
  props: {
    text: String,
    tweetDate: String
  },
 data () {
    return {
      singleTweet: this.text,
      menuArray: []
    };
  },
  mounted: function() {
    //this.singleTweet = this.text;
    //console.log(this.singleTweet);
    this.menuArray = this.text.split("\n");
    for (let i = 0; i < this.menuArray.length; i++) {
      this.menuArray[i] = this.menuArray[i].replace(/&amp/g, '&').replace('&;', '&');
    }
    //let cutStr = s.indexOf('+');
    //console.log(this.menuArray);
    
  }
};
</script>

<style>
.tweetLines {
  white-space: pre-wrap;
}
.menuTable {
  border: 1px solid;
    border-spacing: 0;
    max-width: 380px;
}
th,td {
    border: 1px solid;
    font-family: arial;
    font-size: 17px;
}
.dateTitle {
  border: 3px solid;
}
</style>
