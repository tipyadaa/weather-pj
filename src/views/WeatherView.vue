<template>
    <div class="d-flex justify-content-center "  >
  <div class="card w-75 mb-3 text-center" style="background-color: rgb(133, 218, 255);">
    <div class="card-body">
      <h1 class="card-title" style="color: rgb(0, 0, 0);" ><i class="fa-solid fa-cloud-sun-rain"></i> WEATHER</h1>
      lat : <input type="text" v-model="latA" class="shadow-sm  mb-2 bg-body-tertiary rounded form-control-col-4">
      long : <input type="text" v-model="longA" class="shadow-sm  mb-5 bg-body-tertiary rounded form-control-col-4">
      <button @click="fetchPosts" class="btn  m-2" style="background-color:floralwhite ;color: black; "><i class="fa-solid fa-magnifying-glass"></i></button>
    </div>
  </div>
</div>


  
<div class="row container-fluid d-flex justify-content-center" >
  <div class="card col-4 m-2" style="width: 18rem;" v-for="(i,index) in items.list" :key="index">
  <div class="card-body --bs-light-border-subtle" >
    <h5 class="card-title"><img :src="`https://openweathermap.org/img/wn/`+ i.weather[0].icon +`@2x.png`" class="card-img" alt="..." style="max-width: 140px; "></h5>
    <p class="card-text"><i class="fa-solid fa-calendar-days"></i> Date : {{ i.dt_txt }}</p>
    <p class="card-text"><i class="fa-solid fa-tree-city"></i> Name : {{items.city.name}}</p>
    <p class="card-text"><i class="fa-solid fa-temperature-quarter"></i> Temp : {{ i.main.temp}}&deg;C</p>
    <p class="card-text"><i class="fa-solid fa-mountain-sun"></i> description : {{ i.weather[0].description }}</p>
  </div>
</div>
</div>
    



</template>

<script setup>
import axios from "axios";
import { ref } from "vue";

//const url = ref("https://jsonplaceholder.typicode.com/post/"+id.value);

const items = ref({});
//const lat= ref('14.09237175538297');
//const long= ref('99.41506128383799');
const apikey=ref("65850a0675e831f5a99bacf401f052e9");

const latA = ref();
const longA = ref();




//const url = ref('https://api.openweathermap.org/data/2.5/forecast?lat=14.09237175538297&lon=99.41506128383799&appid=65850a0675e831f5a99bacf401f052e9');


function fetchPosts() {
    const url = ref('https://api.openweathermap.org/data/2.5/forecast?lat='+latA.value+'&lon='+longA.value+'&appid='+apikey.value+'&units=metric');
 axios
 .get(url.value)
 .then((response) => {
 items.value = response.data;
 console.log(items.value)
 })
 .catch((err) => {
 console.log(err);
 });
}


</script>
<style scoped>


</style>