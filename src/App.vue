<script setup>

import { computed, onMounted, ref } from 'vue';
import BlogPost from './components/BlogPost.vue';
import PaginationButtons from './components/PaginationButtons.vue';
import LoadingSpinner from './components/LoadingSpinner.vue'

const posts = ref([])
const favorite = ref('')
const postPerPage = 10;
const start = ref(0);
const end = ref(postPerPage);
const loading = ref(true);

const prev = () => {
  console.log('working')
  start.value -= postPerPage;
  end.value -= postPerPage
}

const next = () => {
  console.log('working')
  start.value += postPerPage;
  end.value += postPerPage
}

const changeFavorite = (title) => {
  favorite.value = title;
}

const url = 'https://jsonplaceholder.typicode.com/posts';
// OPCION 1 HACER UN ASYNC AWAIT

const fetchData = async () => {
  try {
    const res = await fetch(url)
    posts.value = await res.json()
  }
  catch (e) {
    console.log(e)
  }
  finally {
    setTimeout(() => {
      loading.value = false;
    }, 1500)
  }
}
fetchData();

// OPCION 2 HACER UN FETCH CON .THEN

// fetch(url)
//   .then(data => data.json())
//   .then(res => posts.value = res)
//   .catch(err => console.log(err))
//   .finally(() => {
//     setTimeout(() => {
//       loading.value = false;
//     }, 1500)
//   })

// OPCION 3 HACER UN ONMOUNTED

// onMounted(()=> {
//   fetchData()
// });


// Alternative to postLength is directly use posts.length
const postsLength = computed(() => posts.value.length)

</script>


<template>
  <div>
    <h1 class="text-center text-2xl">WELCOME TO MY POSTS APP</h1>
    <PaginationButtons @next="next" @prev="prev" :start="start" :end="end" :postsLength="postsLength" />
    <LoadingSpinner v-if="loading" />
    <BlogPost v-else v-for='post in posts.slice(start, end)' :key='post.id' :id='post.id' :title="post.title"
      :body="post.body" @changeFavoriteName="changeFavorite"></BlogPost>
  </div>
  <h2 class="text-center text-2xl pt-3">Selected post: {{ favorite }}</h2>
</template>