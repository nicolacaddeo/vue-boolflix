<template>
  <div id="app">
    <header>
      <h1>Boolfix</h1>
      <InputComponent @search="searchFilm"/>
    </header>
  </div>
</template>

<script>
  import {apiKey} from '@/data/env.js'
  import axios from 'axios'
  import InputComponent from '@/components/InputComponent.vue'
  
  
  export default {
  components: {
    InputComponent
},
  data() {
    return {
      apiKey
    }
  },
  created() {
    
  },
  methods: {
    searchFilm(searchedFilm) {
      axios.get(`https://api.themoviedb.org/3/search/movie?api_key=${apiKey}&query=${searchedFilm}&language=it-IT`)
      .then(({status, data})=>{
      if (status === 200) {
        console.log(data);
        
      }
    })
    }
  }
}
</script>

<style lang="scss">
@import './style/main_style.scss';

header {
  height: 10vh;
  padding: 1.5rem;
  background-color: #111;
  display: flex;
  justify-content: space-between;
  align-items: center;
  h1 {
    color: #990000;
    text-transform: uppercase;
  }
}
</style>
  
    