<template >

<tr :key="entry.id" v-for="entry in entries" class="entry">
 <Entry @delete-entry="onDelete" @edit-entry="editEntry" :entry="entry"/>
</tr>

</template>
<script>


import App from '@/App.vue';
import Entry from './Entry.vue';

export default{
    name:'Entries',
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

        },
        editEntry(sImage,sItem,id){
            this.$emit('edit-entry',sImage,sItem,id)
        }
    }
    ,
    emits:['delete-entry','edit-entry']

}
    



</script>
<style>
.entry{

padding: 5%;
width: 100%;
margin-bottom: 20px;

}
</style>