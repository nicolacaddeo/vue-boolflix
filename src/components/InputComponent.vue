<template>
  <div>
    <input type="text" v-model="searchedFilm">
    <button @click="$emit('search', searchedFilm)">Search</button>
  </div>
</template>

<script>
export default {
    name: 'InputComponent',
    data(){
        return{
            searchedFilm: ''
        }
    }
}
</script>

<style scoped lang="scss">
    input {
        margin-right: 1rem;
        padding: .2rem .5rem;
    }
    button {
        padding: .2rem .5rem;
    }
</style>