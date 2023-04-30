<script setup>

import { ref } from 'vue';
import BlogPost from './components/BlogPost.vue';


const posts = ref([
  {id:1, title: 'Campeonato 1', text:'Copa merecimiento 2009'},
  {id:2, title: 'Campeonato 2', text:'Copa lloron 2013'},
  {id:3, title: 'Campeonato 3', text:'Copa equipo diminuto 2014'},
])

const favorite = ref('')

const changeFavorite = (title) => {
  favorite.value = title;
}

</script>


<template>
  <div>
    <h1>APP</h1>
    <h2 class="text-center text-2xl underline">Mi loved campeonatos: {{ favorite }}</h2>
    <BlogPost 
    v-for= 'post in posts'
    :key='post.id'
    :title="post.title"
    :text="post.text"
    @changeFavoriteName="changeFavorite"
    ></BlogPost>
  </div>
</template>