<template>
    <header>
        <h1>{{title}}</h1>
        <Button @toggle-add-row= "$emit('toggle-add-row')" :color="showAddRow?'red':'green'" :btext="showAddRow ? 'Close':'Add Row'" />
    </header>
</template>
<script>
import Button from "./Button.vue";
export default {
    name: "Header",
    props: {
        title:String,
        showAddRow: Boolean
    },
    components :{
        Button
    },
    emits:['toggle-add-row'],
}
</script>
<style scoped>
header{
    display: flex;
  justify-content: space-between;
  align-items: center;
  margin-bottom: 20px;
    
}
</style>