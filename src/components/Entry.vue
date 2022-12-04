<template>

          <td>
            <img :src='entry.image' class="image" />
          </td>

          <td>
            <div class="container"> 
              <h3>{{entry.select}}</h3>
            </div>
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
            // console.log('entry has the valuse now ----->',sImage,sItem,this.entry.id)
            if(!sImage){
                sImage=this.entry.image

            }
            if(!sItem){
                sItem=this.entry.select

            }
            this.$emit('edit-entry',sImage,sItem,this.entry.id)
            
            
        }
    },
    emits:['delete-entry','edit-entry','selctedImage']
}
</script>
<style scoped>
.image{
  height: 200px;
  width: 200px;
  border: 1px solid;
  margin: 1.5rem;
}
.cell{
  width: 100%;
}
.container {
  max-width: 90%;
  margin: 30px auto;
  overflow: auto;
  min-height: 80px;
  border: 2px solid steelblue;
  padding: 30px;
  border-radius: 5px;
}
</style>