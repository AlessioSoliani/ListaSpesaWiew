<script setup>
import { computed, onMounted, ref } from "vue";
import axios from 'axios';


let products = ref( [] );

let completedProducts = computed(() => products.value.filter(p => p.completed).length);
let toDoProducts = computed(() => products.value.filter(p => !p.completed).length);




let inputProduct =ref('');


onMounted(()=>{
  axios.get('http://localhost:3000/products').then((res)=>{
    products.value = res.data;
  })
})


function onAddProduct(event) {
  // console.log(event.target.value);
  let nameProduct = event.target.value;
  if(nameProduct.trim()==='')return;
  let newProduct = {
    name: nameProduct,
    completed: false,
    
  }   
  

  axios.post('http://localhost:3000/products', newProduct).then((res) => {
    products.value = [...products.value, res.data];
    inputProduct.value =''; 
    console.log(res.data);
  })

}

function toggleCompleted(item) {
  axios.patch(`http://localhost:3000/products/${item.id}` , item ).then((res) => {
    console.log(res.data);
  })

}

function deleteProduct(productId){  
axios.delete(`http://localhost:3000/products/${productId}`).then((res) =>{
  products.value = products.value.filter(p => p.id != productId);
})
}
</script>


<template>
   <!--sezione per aggiungere un nuovo prodotto  -->
   <div class="w-full md:w-2/5 mx-auto my-4">
      <label class="input rounded-lg input-bordered flex items-center gap-2">
        <input type="text" v-model="inputProduct" @keyup.enter="onAddProduct($event)" class="grow" placeholder="ad new product"/>
        <kbd class="kbd kbd-sm bg-violet-500 hover:bg-violet-600 active:bg-violet-700 focus:outline-none focus:ring focus:ring-violet-300 text-white rounded-md shadow-md  m-1">Enter</kbd>
      </label>
   </div>

<!-- completati e da fare -->
          <div class="w-full md:w-2/5 mx-auto my-4">
            <div class="flex justify-around">
              <button class="btn btn-active btn-neutral">
                <div class="badge">{{ completedProducts }}</div> products taken
              </button>
              <button class="btn btn-active btn-neutral">
                <div class="badge">{{ toDoProducts }}</div>products to take
              </button>
          
            </div>
          </div>

    <!-- lista prodotti -->
  <div class="w-full md:w-2/5 mx-auto border border-neutral rounded-lg">
    <div v-for="product in products" :key="product.id" class="flex justify-between">
          <!-- icona e nome prodotto -->

         <div class="flex items-center">
            <button class="btn btn-square btn-ghost" @click="deleteProduct(product.id)" >
              <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="1.5" stroke="currentColor" class="w-6 h-6">
              <path stroke-linecap="round" stroke-linejoin="round" d="m14.74 9-.346 9m-4.788 0L9.26 9m9.968-3.21c.342.052.682.107 1.022.166m-1.022-.165L18.16 19.673a2.25 2.25 0 0 1-2.244 2.077H8.084a2.25 2.25 0 0 1-2.244-2.077L4.772 5.79m14.456 0a48.108 48.108 0 0 0-3.478-.397m-12 .562c.34-.059.68-.114 1.022-.165m0 0a48.11 48.11 0 0 1 3.478-.397m7.5 0v-.916c0-1.18-.91-2.164-2.09-2.201a51.964 51.964 0 0 0-3.32 0c-1.18.037-2.09 1.022-2.09 2.201v.916m7.5 0a48.667 48.667 0 0 0-7.5 0" />
              </svg>
            </button>
            <span class="label-text" :class="{ 'line-through text-accent' : product.completed }">{{product.name}}</span>
         </div>
         
          <!-- checkbox -->
       <label class="cursor-pointer label">
         <input type="checkbox"  class="checkbox checkbox-secondary mr-4" @change="toggleCompleted(product)" v-model="product.completed" :checked="product.completed" />
       
       </label>
      
    </div>
  </div>

</template>


