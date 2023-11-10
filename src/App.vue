<script setup>
import { RouterLink, RouterView } from 'vue-router'

</script>

<template>
 

  <RouterView />
</template>

<style >
h1 {
  font-family: 'Playfair Display', serif;
}

p {
  font-family: 'Jost', sans-serif;
}

.btn1{
  background: #dcf147;
  padding: 10px 20px;
  border: none;
  border-radius: 5px;
}
input{
  padding: 10px 20px;
  color: white;
  border-radius: 5px;
  background: rgba( 255, 255, 255, 0.15 );
  backdrop-filter: blur( 20px );
  -webkit-backdrop-filter: blur( 20px );
  border: 1px solid rgba( 255, 255, 255, 0.18 );
}
.btn2{
 
  padding: 10px 20px;
  color: white;
  border-radius: 5px;
  background: rgba( 255, 255, 255, 0.15 );
  backdrop-filter: blur( 20px );
  -webkit-backdrop-filter: blur( 20px );
  border: 1px solid rgba( 255, 255, 255, 0.18 );
}


</style>
