<template>
    
      <ButtonTwo @edit-entry="dialog=true" color="blue" text="EDIT"  btnId="2" />
  
      <v-dialog
        v-model="dialog"
      >
        <v-card>
            <v-card-item>
      <div>
        <div class="text-overline mb-1">
          Editing Entry 
        </div>
        <div class="text-h6 mb-1">
         <Image @selcted-image="selectedImage"/>
        </div>
        <div class="text-caption"><DropList @selected-item="ItemSelected" /></div>
      </div>
    </v-card-item>
          <v-card-actions>
            <v-btn color="green"  @click="saving"> Save</v-btn>
            <v-btn color="red"  @click="dialog = false">Close Dialog</v-btn>
          </v-card-actions>
        </v-card>
      </v-dialog>
    
  </template>
  <script>
import DropList from './DropList.vue';
import Image from './Image.vue';
import ButtonTwo from './ButtonTwo.vue';

  export default {
    name:'Dialog',
    data() {
        return {
            dialog: false,
            sImage:"",
            sItem:""
        };
    },
    components: { Image, DropList ,ButtonTwo},
    methods:{
        
        selectedImage(image){
        console.log('image is here=====>', image)
        this.sImage=image
        },
        ItemSelected(item){
            console.log("item is here=======>",item)
            this.sItem=item
        },
        saving(dialog,sItem,sImage){
            this.dialog = false
            console.log("-----> new values",this.sImage,this.sItem)
            this.$emit('saving',this.sImage,this.sItem)
        },

        
    },
    emits:['saving']
}
</script>