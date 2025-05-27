<script setup>
import BotonContador  from './components/BotonContador.vue';
import BlogPost from './components/BlogPost.vue';
import {ref} from 'vue';

const arrayPost = ref([]);

fetch("https://jsonplaceholder.typicode.com/posts")
  .then(response => response.json())
  .then(data => (arrayPost.value = data))

</script>

<template>
  <div class="container" >
  <h1>Componentes</h1>
  <br>
  <BotonContador/>
  <br>
  <br>
 <div class="container">
  <BlogPost
  v-for="post in arrayPost"
  :key="id"
  :titulo="post.title"
  :id="post.id"
  :contenido="post.contenido" 
  class="mt-2"
  />
 </div>
  </div>
</template>

<style>

</style>