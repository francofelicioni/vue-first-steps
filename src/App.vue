<script setup>
import BlogPost from './components/BlogPost.vue';
import Counter from './components/Counter.vue';
</script>


<template>
  <div  class="flex flex-col justify-center items-center p-10">
    <h1 class="mb-10 text-4xl m-3 text-center w-fit"> YEARS WITHOUT HURACAN´T CAMPEON</h1>
    <Counter />
  </div>

  <div>
    <h2 class="text-center text-2xl">Palmares de buri en su historia:</h2>
    <BlogPost id='1' title="Campeon:" text="Copa merecimiento 2009" color/>
    <BlogPost id='2' title="Campeon:" text="Copa lloron 2013" fontColor="red"/>
    <BlogPost id='3' title="Campeon:" text="Copa vi a mi clasico campeon libertadores 2014"/>
  </div>
</template>