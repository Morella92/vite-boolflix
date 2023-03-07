<template>
  <div class="container">
    <Header @search="fetchMovies" />
    <div v-if="movies.length > 0 || series.length > 0">
      <h2>Film:</h2>
      <ul>
        <li v-for="movie in movies" :key="movie.id">
          <h3>{{ movie.title }}</h3>
          <p>Titolo originale: {{ movie.original_title }}</p>
          <p>Lingua: {{ movie.original_language }}</p>
          <p>Voto: {{ movie.vote_average }}</p>
        </li>
      </ul>
  
      <h2>Serie TV:</h2>
      <ul>
        <li v-for="serie in series" :key="serie.id">
          <h3>{{ serie.name }}</h3>
          <p>Titolo originale: {{ serie.original_name }}</p>
          <p>Lingua: {{ serie.original_language }}</p>
          <p>Voto: {{ serie.vote_average }}</p>
        </li>
      </ul>
    </div>
  </div>
</template>

<script>
  import Header from './components/Header.vue';
  import axios from 'axios';

  export default {
    components: {
      Header
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
  @use './style/general.scss'
</style>
