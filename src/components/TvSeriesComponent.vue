<template>
  <div class="card">
    <div class="poster">
        <img :src="`https://image.tmdb.org/t/p/w185${posterPath}`">
    </div>
    <div class="info">
        <h3>{{ title }}</h3>
        <p>Original Title: {{ originalTitle }}</p>
        <p>Original Language: <img class="flag" :src="getFlag()" alt="language"></p>
        <p>Vote: {{ vote }}</p>
    </div>
  </div>
</template>

<script>
export default {
    name: 'TvSeriesComponent',
    props: {
        title: String,
        originalTitle: String,
        language: String,
        vote: Number,
        posterPath: String
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
        width: 50vw;
        border: 1px solid #111;
        padding: 1rem;
        margin: 1rem 0;
        line-height: 2rem;
        display: flex;
        .poster {
            margin-right: 2rem;
        }
        .flag {
            width: 20px;
            vertical-align: middle;
        }
    }
</style>
        