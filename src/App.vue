<script >
  import axios from 'axios'
  import store from './store'
  import Header from './components/Header.vue' 

  export default {

    components:{
      Header
    },
    data(){
      return{
        store
      }
    },
    methods:{
      fetchMovies(){

        const movies = this.store.movies
        const series = this.store.series
        const userSearch = this.store.userSearch

        //faccio la chiamata solo se l'input viene compilato
        if(userSearch !== ''){

          //ricerco il film
          axios
          .get('https://api.themoviedb.org/3/search/movie?api_key=ba0d841780bc45e2866779bbc2a8e4b2&query=m&language=it-IT')

          .then((res) =>{
              movies = res.data.results
          })

          //ricerco la serie
          axios
          .get('https://api.themoviedb.org/3/search/tv?api_key=ba0d841780bc45e2866779bbc2a8e4b2&query=m&language=it-IT')

          .then((res)=>{
            series= res.data.results
          })
        }
      }

    },

    created(){
      this.fetchMovies()
    }
    
  }
</script>

<template>
  <div>
   <Header/>
  </div>
 
</template>

<style lang="scss">
  @use './style/general.scss'
</style>
