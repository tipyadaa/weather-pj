<template>
    <div>
<h1>A- post page</h1>

<div>
<ul>
    <li>userId = {{items.userId}}</li>
    <li>id = {{items.id}}</li>
    <li>title = {{items.title}}</li>
    <!--<li>body = {{items.body}} </li>-->
    <li >

    </li>

</ul>
</div>
    </div>
</template>

<script setup>
import axios from "axios";
import { ref, onMounted } from "vue";


//รับค่าparameter -->id
import { useRoute } from "vue-router";
const route = useRoute()
const id = parseInt(route.params.id)
console.log("ID"+id.value);
const items = ref({});
//const url = ref("https://jsonplaceholder.typicode.com/posts");
const url = ref("https://jsonplaceholder.typicode.com/post/"+route.params.id);
function fetchPosts() {
 axios
 .get(url.value)
 .then((response) => {
 items.value = response.data;
 })
 .catch((err) => {
 console.log(err);
 });
}
onMounted(fetchPosts);
</script>

<style scoped>

</style>