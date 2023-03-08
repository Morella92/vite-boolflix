<template>
    <ul class="grid text-color">
        <li v-for="movie in movies" :key="movie.id">
            <img :src="getImageUrl(movie.poster_path)" :alt="movie.name">
            <h3 class="card-title">{{ movie.title }}</h3>
            <p class="p-cards">Titolo originale: {{ movie.original_title }}</p>
            <!-- <p>Lingua: {{ movie.original_language }}</p> -->
            <p class="p-cards">Lingua:
                <i v-if="movie.original_language" :class="'flag-icon flag-icon-' + movie.original_language.toLowerCase()"></i>
                <span v-else>{{ movie.original_language }}</span>
            </p>
            <!-- <p>Voto: {{ movie.vote_average }}</p> -->
            <p class="p-cards">Voto: 
                <span v-if="movie.vote_average" class="stars">
                    <i v-for="n in Math.ceil(movie.vote_average / 2)" class="fas fa-star"></i>
                    <i v-for="n in 5 - Math.ceil(movie.vote_average / 2)" class="far fa-star"></i>
                </span>
                <span v-else class="stars">
                    <i v-for="n in 5" class="far fa-star"></i>
                </span>
            </p>
        </li>
    </ul>
  
    <ul class="grid text-color">
        <li v-for="serie in series" :key="serie.id">
            <img :src="getImageUrl(serie.poster_path)" :alt="serie.name">
            <h3 class="card-title">{{ serie.name }}</h3>
            <p class="p-cards">Titolo originale: {{ serie.original_name }}</p>
            <!-- <p>Lingua: {{ serie.original_language }}</p> -->
            <p class="p-cards">Lingua:
                <i v-if="serie.original_language" :class="'flag-icon flag-icon-' + serie.original_language.toLowerCase()"></i>
                <span v-else>{{ serie.original_language }}</span>
            </p>
            <!-- <p>Voto: {{ serie.vote_average }}</p> -->
            <p class="p-cards">Voto: 
                <span v-if="serie.vote_average" class="stars">
                    <i v-for="n in Math.ceil(serie.vote_average / 2)" class="fas fa-star"></i>
                    <i v-for="n in 5 - Math.ceil(serie.vote_average / 2)" class="far fa-star"></i>
                </span>
                <span v-else class="stars">
                    <i v-for="n in 5" class="far fa-star"></i>
                </span>
            </p>
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

        methods: {
            getImageUrl(posterPath) {
                const baseUrl = 'https://image.tmdb.org/t/p/w342';
                const defaultImage = 'https://via.placeholder.com/342x513.png?text=No+Image+Available';

                if (posterPath) {
                    return `${baseUrl}${posterPath}`;
                } else {
                    return defaultImage;
                }
            }
        }
    }
</script>


<style lang="scss" scoped>
    .grid{
        display: grid;
        grid-template-columns: repeat(5,1fr);
        gap: 30px;
        padding-top: 30px;
    }

    .text-color{
        color: white;
    }

    .card-title{
        font-size: 25px;
    }

    .p-cards{
        font-size: 20px;
    }
    .stars{
        color: yellow;
    }
</style>