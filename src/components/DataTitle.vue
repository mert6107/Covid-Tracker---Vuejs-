<template>
  <div class="text-center mt-3">
    <h2 class="text-3xl font-bold">{{prop.text}}</h2>
    <div class="text-2xl mt-4 mb-10">
      {{prop.dataDate}}
    </div>
  </div>
</template>

<script setup>
import { computed } from "@vue/runtime-core";

  const prop = defineProps({text:String,dataDate:String});

</script>