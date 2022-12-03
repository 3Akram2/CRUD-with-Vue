<template>

          <td>
            <img :src='entry.image' class="image" />
          </td>
          <td > 
              <h3>{{entry.select}}</h3>
          </td>
          <td> 
            <ButtonTwo @delete-entry = "onDelete" color="red" text="delete" btnId="1" /> 
            <Dialog @saving="saveIng" />
            </td>
            

        
</template>
<script>
import ButtonTwo from './ButtonTwo.vue';
import Dialog from './Dialog.vue';
import DropList from './DropList.vue';



export default{
    data() {
        return {
            isEditing:false
            
        };
    },
    name: "Entry",
    props:{
        entry:Object,
    },
    components:{
    ButtonTwo,
    DropList,
    Dialog

}
    ,
    methods:{
        onDelete(){
        
            this.$emit('delete-entry',this.entry.id)
        },
        saveIng(sImage,sItem){
            console.log('entry has the valuse now ----->',sImage,sItem,this.entry.id)
            this.$emit('edit-entry',sImage,sItem,this.entry.id)
            
            
        }
    },
    emits:['delete-entry','edit-entry','selctedImage']
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
  width: 100%;
}
</style>