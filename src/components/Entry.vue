<template>

          <td>
            <img :src='entry.image' class="image" />
          </td>
          <td > 
              <h3>{{entry.select}}</h3>
          </td>
          <td> <ButtonTwo @delete-entry = "onDelete" color="red" text="delete" btnId="1" /> <ButtonTwo color="blue" text="edit" btnId="2"  /> </td>

        
</template>
<script>
import ButtonTwo from './ButtonTwo.vue';
import DropList from './DropList.vue';


export default{
    data() {
        return {
            
        };
    },
    name: "Entry",
    props:{
        entry:Object,
    },
    components:{
    ButtonTwo,
    DropList,

}
    ,
    methods:{
        onDelete(){
        
            this.$emit('delete-entry',this.entry.id)
        }
    },
    emits:['delete-entry']
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