<template>
  <v-app>
    <v-main>

      <div class="container">
        <Header @toggle-add-row= 'toggleAddRow' title='Title' :showAddRow="showAddRow" />
        <div  v-if="showAddRow">
            <AddRow @add-row="addRow"/>
        </div>
        <Table @delete-entry="deleteEntry" :entries="entries"/>
      </div>
      
    
    
    
    </v-main>
  </v-app>
</template>

<script>
import Header from "./components/Header.vue"
import AddRow from "./components/AddRow.vue"
import Table from "./components/Table.vue"
import Button from "./components/Button.vue"
import DropList from "./components/DropList.vue"
import Image from "./components/Image.vue"

export default {
  name: 'App',

  components: {
Table,
DropList,
Button,
Image,
AddRow,
Header,
  },

  data: () => ({
    showAddRow: false,
    entries:[]
  }),

  methods:{
    toggleAddRow(){
     this.showAddRow=!this.showAddRow;
     
    }, 
   addRow(entry){
   this.entries=[...this.entries,entry]

   },
   deleteEntry(id){
    if(confirm('Are you sure?')){
      this.entries=this.entries.filter((entry)=>entry.id !==id)
    }

   }
  

}, created(){

this.entries= [
    {
        "id":"1",
        "image": "https://www.global-adventures.us/wp-content/uploads/2021/10/shutterstockRF_520475221.jpg",
        "select":"Florida"
    },
    {
        "id":"2",
        "image": "https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcQ-KJ9Rk2YJHFDDJUZwey03lIhI7-V0d4srtrpbW7SJ&s",
        "select":"Georgia"
    },
    {
        "id":"3",
        "image": "https://static3.depositphotos.com/1007581/227/i/600/depositphotos_2272322-stock-photo-soybean-field.jpg",
        "select":"Nebraska"
    }

    ]

}
}
</script>
<style>
.container {
  max-width: 90%;
  margin: 30px auto;
  overflow: auto;
  min-height: 300px;
  border: 1px solid steelblue;
  padding: 30px;
  border-radius: 5px;
}

</style>
