<template>
    <ul class="grid">
        <li v-for="movie in movies" :key="movie.id" class="item">

            <img :src="getImageUrl(movie.poster_path)" :alt="movie.name" class="card-poster">
           
            <div class="card-details">
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
                <p class="overview p-cards">Overview: {{ movie.overview }}</p> 
            </div>
        </li>
    </ul>
  
    <ul class="grid">
        <li v-for="serie in series" :key="serie.id" class="item">

            <img :src="getImageUrl(serie.poster_path)" :alt="serie.name" class="card-poster">

            <div class="card-details">
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
                <p class="overview p-cards">Overview: {{ serie.overview }}</p> 
            </div>
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

    .item{
        position: relative;

        &:hover .card-poster {
            filter: opacity(0.1);
        }
        &:hover .card-details{
            display: block;
        }
    }
    .card-details{
        width: 100%;
        height: 100%;
        overflow-y: scroll;
        position: absolute; 
        top: 0;
        bottom: 0;
        transform: translateX(50%,-50%);
        padding: 10px;
        color: white;
        display: none;
    }

    .card-details::-webkit-scrollbar{
        display: none;
    }
    .card-title{
        font-size: 25px;
    }

    .p-cards{
        font-size: 18px;
    }
    .stars{
        color: yellow;
    }
</style>