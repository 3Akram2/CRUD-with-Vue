<template >

<tr :key="entry.id" v-for="entry in entries" class="entry">
 <Entry @delete-entry="onDelete" :entry="entry"/>
</tr>

</template>
<script>


import Entry from './Entry.vue';

export default{
    data() {
        return {
            
        }
    },
    components:{
   Entry
    
},
    props:{
        entries:Array
    },
    methods:{
        onDelete(id){
            this.$emit("delete-entry",id)

        }
    }
    ,
    emits:['delete-entry']

}
    



</script>
<style>
.entry{

padding: 5%;
width: 100%;
margin-bottom: 20px;

}
</style>