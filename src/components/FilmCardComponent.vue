<template>
  <div class="card">
    <h3>{{ title }}</h3>
    <p>Original Title: {{ originalTitle }}</p>
    <p>Original Language: <img :src="getFlag()" alt="language"></p>
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
    },
    data() {
        return {
            country: ''
        }
    },
    methods: {
        getFlag() {
            this.country = this.language;
            if (this.country === 'en') {
                this.country = 'gb'
            } else if (this.country === 'ko') {
                this.country = 'kr'
            }
            return `https://flagicons.lipis.dev/flags/1x1/${this.country}.svg`
        }
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
        line-height: 2rem;
        img {
            width: 20px;
            vertical-align: middle;
        }
    }
</style>
       