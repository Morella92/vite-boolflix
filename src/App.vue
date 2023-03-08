<template>
  <header class="header">
    <div class="container">
      <Header @search="fetchMovies"/>
    </div>
  </header>
  <main class="main">
    <div class="container">
      <div v-if="movies.length > 0 || series.length > 0">
        <Movie :movies="movies" :series="series"/>
      </div>
    </div>
  </main>
</template>

<script>
  import axios from 'axios';
  import Header from './components/Header.vue';
  import Movie from './components/Movie.vue'

  export default {
    components: {
      Header,
      Movie, 
    },
    data() {
      return {
        movies: [],
        series: [],
      }
    },
    methods: {

      fetchMovies(userSearch) {
        axios
        .get(`https://api.themoviedb.org/3/search/movie?api_key=ba0d841780bc45e2866779bbc2a8e4b2&query=${userSearch}`)
        .then((res) => {
          this.movies = res.data.results
        })
        .catch(err => {
          this.movies = []
        })

        axios
        .get(`https://api.themoviedb.org/3/search/tv?api_key=ba0d841780bc45e2866779bbc2a8e4b2&query=${userSearch}`)
        .then((res) => {
          this.series = res.data.results
        })
        .catch(err =>{
          this.series = []
        })
      }
    }
  }
</script>


<style lang="scss">
  @use './style/general.scss';

  .header{
    background-color: black;
    min-height: 70px;
  }

  .main{
    background-color: rgb(39, 36, 36);
  }
</style>
