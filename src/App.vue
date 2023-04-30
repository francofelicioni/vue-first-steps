<script setup>

import { ref } from 'vue';
import BlogPost from './components/BlogPost.vue';
import Counter from './components/Counter.vue';

const posts = ref([
  {id:1, title: 'Campeonato', text:'Copa merecimiento 2009'},
  {id:2, title: 'Campeonato', text:'Copa lloron 2013'},
  {id:3, title: 'Campeonato', text:'Copa equipo diminuto 2014'},
])


</script>


<template>
  <div  class="flex flex-col justify-center items-center p-10">
    <h1 class="mb-10 text-4xl m-3 text-center w-fit"> YEARS WITHOUT HURACAN´T CAMPEON</h1>
    <Counter />
  </div>

  <div>
    <h2 class="text-center text-2xl underline">Palmares de buri en su historia:</h2>
    <BlogPost 
    v-for= 'post in posts'
    :key='post.id'
    :title="post.title"
    :text="post.text"
    ></BlogPost>
  </div>
</template>