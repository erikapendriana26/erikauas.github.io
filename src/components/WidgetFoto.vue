<template>
    <div>
      <h2>Foto</h2>
      <div id="image-container">
        <img :src="imagePath" alt="Foto" />
      </div>
      <input type="file" accept="image/*" @change="handleImageUpload" />
    </div>
  </template>
  
  <script>
  export default {
    data() {
      return {
        imagePath: "", // Path foto yang akan ditampilkan
      };
    },
    methods: {
      handleImageUpload(event) {
        const file = event.target.files[0];
        const reader = new FileReader();
  
        reader.onload = () => {
          this.imagePath = reader.result;
        };
  
        if (file) {
          reader.readAsDataURL(file);
        }
      },
    },
  };
  </script>
  
  <style scoped>
  #image-container {
    text-align: center;
  }
  </style>
  