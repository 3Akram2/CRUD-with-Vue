<template>
 <v-select
 
  label="Select Item"
  v-model="selectItem"
  :items="items"
  v-on:update:menu="onItemSelcted"
  :selected="items[1]"
  
>

</v-select>

</template>


<script>
export default {
    
  data () {
    return {
      selectItem: '',
      items: [
          'Georgia',
          'Florida',
         'Nebraska',
         'California',
         'New York' ,
      ],
    }
    
},
methods:{
  onItemSelcted(selectItem)
    {
      console.log("===============================> worked!!",this.selectItem)
      this.$emit('selected-item',this.selectItem)
      
    }
}  ,


}

</script>
<style>
.drop{
    margin: 5px;
}
</style>

