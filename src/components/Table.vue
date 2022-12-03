<template>
    <v-table >
      <thead>
        <tr>
          <th class="text-left cell">
            Image
          </th>
          <th class="text-left cell">
            Select
          </th>
          <th class="text-left cell" >
            Actions
          </th>
        </tr>
      </thead>
      <tbody >
        <Entries @delete-entry="onDelete" @edit-entry="editEntry" :entries="entries" />
      </tbody>
    </v-table>
  </template>
  <script>

  
import ButtonTwo from './ButtonTwo.vue';

import Entries from "./Entries.vue";


  
  export default {
   
props:{
        entries:Array,
    },
    data() {
        return {
            
        };
    },
    components: { ButtonTwo ,Entries},
    methods:{
      onDelete(id){
        this.$emit("delete-entry",id)

      },
      editEntry(sImage,sItem,id){
        this.$emit('edit-entry',sImage,sItem,id)

      }
    }
}
</script>
<style>
.image{
  height: 200px;
  width: 200px;
  border: 1px solid;
  margin: 1.5rem;
}
.cell{
  width: 30%;
}

</style>