<template>
  <v-app>
    <v-main>

      <div class="container">
        <Header @toggle-add-row= 'toggleAddRow' title='Title' :showAddRow="showAddRow" />
        <div  v-if="showAddRow">
            <AddRow @add-row="addRow"/>
        </div>
        <Table @delete-entry="deleteEntry" @edit-entry="editEntry" :entries="entries"/>



      </div>
      
    
    
    
    </v-main>
  </v-app>
</template>

<script>
import Header from "./components/Header.vue"
import AddRow from "./components/AddRow.vue"
import Table from "./components/Table.vue"

export default {
  name: 'App',

  components: {
Table,
AddRow,
Header,

  },

  data: () => ({
    showAddRow: false,
    entries:[]
  }),

  methods:{
   async fetchEntries(){
      const res = await fetch('api/entries')
      const data=await res.json()
      return data
    },
    async fetchEntry(id){
      const res = await fetch(`api/entries/${id}`)
      const data = await res.json()
      return data

    },
    toggleAddRow(){
     this.showAddRow=!this.showAddRow;
     
    }, 
   async addRow(entry){
    const res=await fetch('api/entries',{
      method:'POST',
      headers:{
        'content-type':'application/json'
      },
      body:JSON.stringify(entry)
    })
   this.entries=[...this.entries,entry]

   },
   async deleteEntry(id){
    if(confirm('Are you sure?')){
      const res=await fetch(`api/entries/${id}`,{
        method:'DELETE'
      })

      res.status===200?this.entries=this.entries.filter((entry)=>entry.id !==id):alert('Error deleting this entry')
    }
       },
     async  editEntry(sImage,sItem,id){
      const entryToEdit=await this.fetchEntry(id)
      const updEntry={...entryToEdit,image:sImage,select:sItem}

        

      const res = await fetch(`api/entries/${id}`, {
        method:'PUT',
        headers: {
          'Content-type': 'application/json',
        },
        body: JSON.stringify(updEntry)
      })
      const data =  await res.json()
      this.entries = this.entries.map((entry)=>
      entry.id===id?{...entry,image:data.image,select:data.select}:entry
      )

      

    }



  

}, 
async created(){

this.entries= await this.fetchEntries()

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




<!-- if(sImage){
  this.entries =this.entries.map((entry)=>
  entry.id==id?{...entry,image:sImage}:entry
  )
}
if(sItem){
this.entries =this.entries.map((entry)=>
  entry.id==id?{...entry,select:sItem}:entry
  ) -->