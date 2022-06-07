<template>
  <div class="container">
    <h3> Items:</h3>
        <div v-for="item in items" v-bind:key="item.ItemCode">
            <form id="formElem">
                <input type="text" name="itemCode" v-model="item.itemcode" disabled />
                <input type="text" name="itemDescription" v-model="item.itemdescription">
                <input type="text" name="technicalGroup" v-model="item.technicalgroup">
                <button type="submit" v-on:click="submitItem(item.itemcode, item.itemdescription, item.technicalgroup)">Submit</button>
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
        .get('http://items.lfa/api/items/getitems')
        .then(res => {
          this.items = res.data;
        })
    },
    methods: {
        submitItem: function (id, desc, grp) {
            axios.put('http://items.lfa/api/items/putitems', {
                itemcode: id,
                itemdescription: desc,
                technicalgroup: grp
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