<template>
    <a >
        <img :src="Logo" alt="Logo" />
      </a>
    
  </template>
  
  <script>
  import Logo from '../assets/Logo.svg'
  export default {
   data(){
     return{
        Logo:Logo
     }
   }
  };
  </script>

  <style scoped>
  @media (max-width:495px) {
    
   img{
      height: 20px;
    }
    }
  </style>