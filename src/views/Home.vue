<template>
  <div class="home">
    
    <p>Length: <input type="text" v-model="newBoat.length"></p>
    <p>height: <input type="text" v-model="newBoat.height"></p>
    <p>name: <input type="text" v-model="newBoat.name"></p>
    <p>direction: <input type="text" v-model="newBoat.direction"></p>
    <button v-on:click="addBoat()">Add Boat</button>
    <hr>
    <hr>
    <div v-for="boat in boats">
      <p>length: {{ boat.length }}</p>
      <p>height: {{ boat.height }}</p>
      <p>name: {{ boat.name }}</p>
      <p>direction: {{ boat.direction }}</p>
      <hr>
    </div>
    <!-- <button v-on:click="download()">Download</button> -->
    <download-csv
        class   = "btn btn-default"
        :data   = "boats"
        name    = "filename.csv">
        Download CSV (This is a slot)
    </download-csv>
<hr>
      <vue-blob-json-csv
        @success="handleSuccess"
        @error="handleError"
        file-type="csv"
        file-name="sample"
        :data="boats"
      >
    <h2>Title</h2>
    <p>csv download</p>
  </vue-blob-json-csv>

  </div>
</template>

<style>
</style>

<script>

import Vue from 'vue'
import JsonCSV from 'vue-json-csv'
import VueBlobJsonCsv from 'vue-blob-json-csv';


Vue.component('downloadCsv', JsonCSV)
Vue.use(VueBlobJsonCsv)


export default {
  
  data: function() {
    return {
      message: "Welcome to Vue.js!",
      boats: [
        {
          length: 2000,
          height: 100,
          name: "eergiven",
          direction: "one"
        }
      ],
      fields: [  
        "length",
        "height",
        "name",
        "direction"
      ],
      newBoat: {
        length: "",
        height: "",
        name: "",
        direction: ""
      }
    };
  },

  created: function() {},
  methods: {
    addBoat: function() {
      this.boats.push(this.newBoat);
      this.newBoat = {
        length: "",
        height: "",
        name: "",
        direction: ""
      }
    },
    download: function() {
      
    }
  }
};
</script>

