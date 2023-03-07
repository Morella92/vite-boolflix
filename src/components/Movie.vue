<template>
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
</template>

<script>
    export default {
        props: {
            movies: {
                type: Array,
            },
            series: {
                type: Array,
            }
        }
    }
</script>


<style lang="scss" scoped>

</style>