<template>
  <div class="home">
    <img alt="Vue logo" src="https://tm.ibxk.com.br/2019/09/30/30091641838086.jpg?ims=900x320">
    <Home />
  </div>
</template>

<script lang="ts">
import { defineComponent } from 'vue';
import Home from '@/components/Home.vue'; 

export default defineComponent({
  name: 'HomeView',
  components: {
    Home,
  },
  
});
</script>
