<template>
  <div class="container">
    <h3> Items:</h3>
    <table class="table">
      <thead>
        <tr>
          <th scope="col">ItemCode</th>
          <th scope="col">ItemDescription</th>
          <th scope="col">TechnicalGroup</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="item in items" v-bind:key="item.ItemCode"> 
          <th scope="row">{{item.ItemCode}}</th>
          <td>{{item.ItemDescription}}</td>
          <td>{{item.TechnicalGroup}}</td>
        </tr>
      </tbody>
    </table> 
  </div> 
</template>

<script>
  import axios from 'axios';
  export default {
    name: 'ItemDetails',
    data() {
      return {
        items: null,
      };
    },
    created: function() {
      axios
        .get('https://my-json-server.typicode.com/danielcontreras-ppg/myjsonserver-lfaitems/items')
        .then(res => {
          this.items = res.data;
        })
    }
  }
</script>

<style>
  h3 {
    margin-bottom: 5%;
  }
</style>