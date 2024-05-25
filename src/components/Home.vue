<script setup>
// Import Vue Router
import { useRouter } from 'vue-router';

// Programmatically navigate to ProductToBuy component
const router = useRouter();
function goToProductToBuy() {
  router.push('/product-to-buy');
}
</script>

<template> 
<div class=" phones flex justify-center">
  <div class="card lg:card-side h-96 bg-base-100 shadow-xl">
     <div class="responsiveImg"  alt="Album"></div>
         <div class=" flex align-center  card-body w-48">
              <h2 class="card-title"> Manage your spending </h2>
              <p>Shopping List, your essential tool for creating and organizing your shopping lists intuitively and quickly, ensuring a stress-free and well-organized shopping experience!</p>
              
         </div>        
   </div>
</div>
<div class="justPhones">
<h1> Manage your spending </h1>
<p>Shopping List, your essential tool for creating and organizing your shopping lists intuitively and quickly, ensuring a stress-free and well-organized shopping experience!</p>
</div>


</template>


