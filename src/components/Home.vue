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
              <h2 class="card-title"> gestisci la tua spesa </h2>
              <p>Shopping List, il tuo strumento essenziale per creare e organizzare le tue liste della spesa in modo intuitivo e veloce, garantendoti un'esperienza di shopping senza stress e ben organizzata!</p>
              
         </div>        
   </div>
</div>
<div class="justPhones">
<h1> Gestisci la tua spesa </h1>
<p>Shopping List, il tuo strumento essenziale per creare e organizzare le tue liste della spesa in modo intuitivo e veloce, garantendoti un'esperienza di shopping senza stress e ben organizzata!</p>
</div>
</template>


