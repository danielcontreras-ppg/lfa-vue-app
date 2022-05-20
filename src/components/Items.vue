<template>
  <div class="container">
    <h3> Items:</h3>
        <div v-for="item in items" v-bind:key="item.ItemCode">
            <form id="formElem">
                <input type="text" name="ItemCode" v-model="item.ItemCode" disabled />
                <input type="text" name="ItemDescription" v-model="item.ItemDescription">
                <input type="text" name="TechnicalGroup" v-model="item.TechnicalGroup">
                <button type="submit">Submit</button>
            </form> 
        </div>
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