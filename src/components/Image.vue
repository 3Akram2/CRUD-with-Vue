<template>
    <v-file-input
     @change="onImageSelcted"
    

      :rules="rules"
      accept="image/png, image/jpeg, image/bmp"
      placeholder="choose an image"
      prepend-icon="mdi-camera"
      label="choose an image"
    >
</v-file-input>
  </template>
<script>
export default {
  name:'Image',
  
  data: () => ({
    selctedImage:null,
    rules: [
      value => {
        return !value || !value.length || value[0].size < 2000000 || 'Avatar size should be less than 2 MB!'
      },
    ],
  }),
  methods:{
    onImageSelcted(event)
    {
     this.selctedImage=URL.createObjectURL(event.target.files[0])
     console.log(this.selctedImage)
     this.$emit('selcted-image',this.selctedImage)
    }

  }
}
</script>