<template>
  <main v-if="!loading">
   <DataTitle :text="title" :dataDate="dataDate"/>
   <DataBoxes :stats="stats" />

   <CountrySelect :countries="countries" @getCountry="getCountryData" />
   <div class="flex justify-center">
     
     <button @click="clearCountry" v-if="stats.Country" class="bg-green-600 text-white rounded w-3/12 p-3 mt-10 mb-10 focus:outline-none hover:bg-green-600">Clear Country</button>
   </div>
  </main>
  <main class="flex flex-col align-center justify-center text-center" v-else>
      <div class="text-gray-500 text-3xl mt-10 mb-6">
        Fetching Data
      </div>
  </main>
  


</template>

<script setup>
import DataTitle from "../components/DataTitle.vue";
import DataBoxes from "../components/DataBoxes.vue";
import CountrySelect from "../components/CountrySelect.vue";
import {onMounted, reactive, ref} from "vue";

const title = ref('Global');
const dataDate = ref('');
const stats =ref({});
const countries = reactive([]);
const loading = ref(true);

const fetchData = async ()=>{
  const res = await fetch('https://api.covid19api.com/summary')
  const data = await res;
  return data.json();
};
const data = onMounted(async ()=>{

  const viruses = await fetchData();
  dataDate.value = viruses.Date;
  stats.value = viruses.Global;
  countries.value = viruses.Countries;
  loading.value = false;
});

const getCountryData = (country) => {
  console.log(country);
  stats.value = country;
  title.value = country.Country;
  
}

const clearCountry = async () => {
  loading.value = true;
  const data = await fetchData();
  title.value = 'Global';
  stats.value = data.Global;
  loading.value = false;
}

</script>
