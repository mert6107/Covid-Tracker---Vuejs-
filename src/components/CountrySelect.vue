<template>
    <select @change="onChange" v-model="selectedData" class="form-select mt-10 block w-full border p-3 rounded">
        <option value="0" >Select Country</option>
        <option v-for="country in prop.countries.value" :key="country.ID" :value="country.ID">{{country.Country}}</option>
    </select>
</template>

<script setup>
import { ref } from "@vue/reactivity";

const emits = defineEmits(["getCountry"]);
const prop = defineProps({countries:Array});
const selectedData = ref(0);
const onChange = () => {
   const country = prop.countries.value.find((i)=> i.ID === selectedData.value);
   //console.log("country",country);
   const action = emits('getCountry', country);
};


</script>