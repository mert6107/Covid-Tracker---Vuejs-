<template>
<div class="flex flex-col items-center">
    <!-- Box 1 -->
  <div class="shadow-md bg-blue-100 p-10 text-center rounded mb-5 w-3/12">
    <h3 class="text-3xl text-blue-900 font-bold mb-4">Cases</h3>    
  
  <div class="text-2xl mb-4">
    <span class="font-bold">New:</span>   
    {{numberWithCommax(prop.stats.NewConfirmed)}}
   </div>  
    <div class="text-2xl mb-4">
    <span class="font-bold">Total:</span>   
    {{numberWithCommax(prop.stats.TotalConfirmed)}}
   </div> 

  </div>  
    <!-- Box 2 -->
  <div class="shadow-md bg-blue-200 p-10 text-center rounded  w-3/12">
    <h3 class="text-3xl text-blue-900 font-bold mb-4">Deaths</h3>    
  
  <div class="text-2xl mb-4">
    <span class="font-bold">New:</span>   
    {{numberWithCommax(prop.stats.NewDeaths)}}
   </div>  
    <div class="text-2xl mb-4">
    <span class="font-bold">Total:</span>   
    {{numberWithCommax(prop.stats.TotalDeaths)}}
   </div> 

  </div> 
</div>        
</template>

<script setup>
const prop = defineProps({stats:Object});
const numberWithCommax = (x) =>{
    return x.toString().replace(/\B(?=(\d{3})+(?!\d))/g, ',');
};

</script>