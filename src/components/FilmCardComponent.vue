<template>
  <div class="card">
    <h3>{{ title }}</h3>
    <p>Original Title: {{ originalTitle }}</p>
    <p>Original Language: {{ language }}</p>
    <p>Vote: {{ vote }}</p>
  </div>
</template>

<script>
export default {
    name: 'FilmCardComponent',
    props: {
        title: String,
        originalTitle: String,
        language: String,
        vote: Number
    }
}
</script>

<style scoped lang="scss">
    .card{
        width: 40vw;
        height: 300px;
        border: 1px solid #111;
        padding: 1rem;
        margin: 1rem 0;
    }
</style>
       