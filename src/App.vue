<template>
  <header class="header">
    <div class="container">
      <Header @search="fetchMovies" />
    </div>
  </header>
  <div class="container">
    <div v-if="movies.length > 0 || series.length > 0">
      <Movie :movies="movies" :series="series"/>
    </div>
  </div>
</template>

<script>
  import Header from './components/Header.vue';
  import axios from 'axios';
  import Movie from './components/Movie.vue'

  export default {
    components: {
      Header, 
      Movie
    },
    data() {
      return {
        movies: [],
        series: [],
      }
    },
    methods: {
      fetchMovies(userSearch) {
        if (userSearch !== '') {
          axios
          .get(`https://api.themoviedb.org/3/search/movie?api_key=ba0d841780bc45e2866779bbc2a8e4b2&query=${userSearch}&language=it-IT`)
          .then((res) => {
            this.movies = res.data.results
          })

          axios
          .get(`https://api.themoviedb.org/3/search/tv?api_key=ba0d841780bc45e2866779bbc2a8e4b2&query=${userSearch}&language=it-IT`)
          .then((res) => {
            this.series = res.data.results
          })
        }
      }
    }
  }
</script>


<style lang="scss">
  @use './style/general.scss';

  .header{
    background-color: rgb(73, 70, 70);
    min-height: 70px;
  }
</style>
