<template>
  <div id="app">

  </div>
</template>

<script>
  import {apiKey} from '@/data/env.js'
  import axios from 'axios'
  
  export default {
  components: {
    
  },
  data() {
    return {
      apiKey
    }
  },
  created() {
    axios.get(`https://api.themoviedb.org/3/movie/550?api_key=${apiKey}`)
    .then(({status, data})=>{
      if (status === 200) {
        console.log(data);
        
      }
    })
  }
}
</script>

<style lang="scss">
@import './style/main_style.scss';

</style>