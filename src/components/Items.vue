<template>
  <div class="container">
    <h3> Items:</h3>
        <div v-for="item in items" v-bind:key="item.ItemCode">
            <form id="formElem">
                <input type="text" name="ItemCode" v-model="item.ItemCode" disabled />
                <input type="text" name="ItemDescription" v-model="item.ItemDescription">
                <input type="text" name="TechnicalGroup" v-model="item.TechnicalGroup">
                <button type="submit" v-on:click="submitItem(item.ItemCode, item.ItemDescription, item.TechnicalGroup)">Submit</button>
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
    created: function () {
      axios
        .get('https://my-json-server.typicode.com/danielcontreras-ppg/myjsonserver-lfaitems/items')
        .then(res => {
          this.items = res.data;
        })
    },
    methods: {
        submitItem: function (id, desc, grp) {
            axios.put('http://localhost/itemsput', {
                ItemCode: id,
                ItemDescription: desc,
                TechnicalGroup: grp
            });
        }
  }  
  }
</script>

<style>
  h3 {
    margin-bottom: 5%;
  }
</style>