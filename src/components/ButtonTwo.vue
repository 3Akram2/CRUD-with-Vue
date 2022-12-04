<template>
    <v-btn 
    
    class="btn"
    v-on:click="buttonAction(btnId)"
  :color='color'
  elevation="11"
  large
  
  
> {{text}}</v-btn>
</template>
<script>
export default{
    name:'ButtonTwo',
    data(){
        return{ id:''
        };
    
    },
    props:{
        text:String,
        color:String,
        btnId:String,
        
    },
    methods:{
        buttonAction(btnId){
            
            
            
            if(btnId==="1"){
                this.$emit("delete-entry")

            }
            else if(btnId==="2"){
                this.$emit('edit-entry')
            }
        }
    }
}

</script>
<style>
.btn{
    margin: 5px;
}
</style>
