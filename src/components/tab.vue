<script setup>

import { ref } from "vue";
import ProductToBuy from'./ProductsToBuy.vue';
import Home from './Home.vue';
let tab = ref(1);
</script>

<template>
  <div class="tabs w-full">
    <!-- tabs -->
    <div class="flex justify-center p-5">
      <button :class="{'btn-neutral' : tab===1}" class="  ml-1.5 rounded-lg btn btn-xs sm:btn-sm md:btn-md lg:btn-lg" @click="tab=1">Home</button>
      <button :class="{'btn-neutral' : tab===2}" class="  ms-1.5 rounded-lg btn btn-xs sm:btn-sm md:btn-md lg:btn-lg" @click="tab=2">Products To Buy</button>
    </div>

    <!-- contenuto -->
    <div class="contents">
      <div v-if="tab == 1" class="py-10 px-6">
        <Home/>
      </div>
      <div v-if="tab == 2" class="py-10 px-6"><productToBuy/></div>
    </div>
  </div>
</template>
