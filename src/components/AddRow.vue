<template>
<form @submit="onSubmit" class="add-form">
    <div class="form-control">
      <label>Add image</label>
      <Image @selcted-image="uploadImage"/>
    </div>
    <div class="form-control">
      <label>Select a choice</label>
      <DropList @selected-item="selectItem"  />
    </div>
    

    <input type="submit" value="Save Row" class="btn btn-block" />
  </form>
</template>
<script>
import DropList from './DropList.vue'
import Image from './Image.vue'
export default {
    name: 'AddRow',
    components:{
      DropList,
Image,
    },
    data(){
        return{
            image:'',
            select: '',
            
        }
    }, 
    methods:{
        uploadImage(selctedImage){
          this.image=selctedImage
          console.log(this.image)
          
        },
        selectItem(selctedItem){
          this.select=selctedItem
          console.log(this.select)
        },
        onSubmit(e){
            e.preventDefault()

            if(!this.image){
                alert("please add a image")
                return


            }
            const newRow={
                id:Math.floor(Math.random()*10000),
                image:this.image,
                select:this.select
                
                
            }

            this.$emit('add-row',newRow)
            //to clear the form 
            this.image=''
            this.select=''
            
        }
    }

}
</script>
<style scoped>
.add-form {
  margin-bottom: 40px;
}
.form-control {
  margin: 20px 0;
}
.form-control label {
  display: block;
}
.form-control input {
  width: 100%;
  height: 40px;
  margin: 5px;
  padding: 3px 7px;
  font-size: 17px;
}
.form-control-check {
  display: flex;
  align-items: center;
  justify-content: space-between;
}
.form-control-check label {
  flex: 1;
}
.form-control-check input {
  flex: 2;
  height: 20px;
}
.btn {
  display: inline-block;
  background: #000;
  color: #fff;
  border: none;
  padding: 10px 20px;
  margin: 5px;
  border-radius: 5px;
  cursor: pointer;
  text-decoration: none;
  font-size: 15px;
  font-family: inherit;
}
.btn:focus {
  outline: none;
}
.btn:active {
  transform: scale(0.98);
}
.btn-block {
  display: block;
  width: 100%;
  
}
</style>

