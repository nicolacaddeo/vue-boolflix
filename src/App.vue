<template>
  <div id="app">
    <header>
      <h1>Boolfix</h1>
      <InputComponent @search="searchFilm"/>
    </header>
    <main>
      <FilmCardComponent v-for="movie in moviesFound" :key="movie.id"
      :title = movie.title
      :originalTitle = movie.original_title
      :language = movie.original_language
      :vote = movie.vote_average 
      :posterPath = movie.poster_path />
      <TvSeriesComponent v-for="serie in tvSeriesFound" :key="serie.id"
      :title = serie.name
      :originalTitle = serie.original_name
      :language = serie.original_language
      :vote = serie.vote_average 
      :posterPath = serie.poster_path />
    </main>
  </div>
</template>

<script>
  import {apiKey} from '@/data/env.js'
  import axios from 'axios'
  import InputComponent from '@/components/InputComponent.vue'
  import FilmCardComponent from './components/FilmCardComponent.vue'
  import TvSeriesComponent from './components/TvSeriesComponent.vue'
  
  export default {
  components: {
    InputComponent,
    FilmCardComponent,
    TvSeriesComponent
},
  data() {
    return {
      apiKey,
      moviesFound: [],
      tvSeriesFound: []
    }
  },
  methods: {
    searchFilm(searchedFilm) {
      axios.get(`https://api.themoviedb.org/3/search/movie?api_key=${apiKey}&query=${searchedFilm}&language=it-IT`)
      .then(({status, data})=>{
      if (status === 200) {
        console.log('data:', data.results);
        this.moviesFound = data.results;
      }
    }),
    axios.get(`https://api.themoviedb.org/3/search/tv?api_key=${apiKey}&query=${searchedFilm}&language=it-IT`)
      .then(({status, data})=>{
        if (status === 200) {
          console.log('data serie tv:', data.results);
          this.tvSeriesFound = data.results;
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
main {
  padding: 2rem;
}
</style>
  
  
    