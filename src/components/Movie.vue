<template>
    <ul class="grid">
        <li v-for="movie in movies" :key="movie.id">
            <h3>{{ movie.title }}</h3>
            <p>Titolo originale: {{ movie.original_title }}</p>
            <!-- <p>Lingua: {{ movie.original_language }}</p> -->
            <p>Lingua:
                <i v-if="movie.original_language" :class="'flag-icon flag-icon-' + movie.original_language.toLowerCase()"></i>
                <span v-else>{{ movie.original_language }}</span>
            </p>
            <p>Voto: {{ movie.vote_average }}</p>
        </li>
    </ul>
  
    <ul class="grid">
        <li v-for="serie in series" :key="serie.id">
            <h3>{{ serie.name }}</h3>
            <p>Titolo originale: {{ serie.original_name }}</p>
            <!-- <p>Lingua: {{ serie.original_language }}</p> -->
            <p>Lingua:
                <i v-if="serie.original_language" :class="'flag-icon flag-icon-' + serie.original_language.toLowerCase()"></i>
                <span v-else>{{ serie.original_language }}</span>
            </p>
            <p>Voto: {{ serie.vote_average }}</p>
        </li>
    </ul>
</template>

<script>
    

    export default {
        props: {
            movies: {
                type: Array,
                required: true
            },
            series: {
                type: Array,
                required: true
            }
        },
    }
</script>


<style lang="scss" scoped>
    .grid{
        display: grid;
        grid-template-columns: repeat(5,1fr);
        gap: 30px;
        margin-top: 30px;
    }
</style>