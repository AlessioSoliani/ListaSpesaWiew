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
  <!-- <div style="  display: flex; justify-content: center; ">
      <div class="hero min-h-screen" style="border-radius: 100%; overflow: hidden; object-fit: cover;  width: 50%; height: auto; background-image: url(./public/supermercato-spesa.jpg);">
        <div class="hero-overlay bg-opacity-60"></div>
        <div class="hero-content text-center text-neutral-content">
          <div class="max-w-md">
            <h1 class="mb-5 text-5xl font-bold">Shopping List</h1>
            <p class="mb-5">Shopping List, il tuo strumento essenziale per creare e organizzare le tue liste della spesa in modo intuitivo e veloce, garantendoti un'esperienza di shopping senza stress e ben organizzata!</p>
           
          </div>
        </div>
      </div>
  </div>    -->

<div class="flex justify-center">
  <div class="card lg:card-side h-96 bg-base-100 shadow-xl" style="width:70%;">
     <div style="width:60%; height: auto; background-repeat: no-repeat; background-image: url(./public/supermercato-spesa.jpg);"  alt="Album"></div>
         <div class=" flex align-center  card-body w-48">
              <h2 class="card-title"> gestisci la tua spesa </h2>
              <p  >Shopping List, il tuo strumento essenziale per creare e organizzare le tue liste della spesa in modo intuitivo e veloce, garantendoti un'esperienza di shopping senza stress e ben organizzata!</p>
              <div class="card-actions justify-end">
              </div>
         </div>        
   </div>
</div>
   
</template>


