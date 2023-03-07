<script>
    import store from '../store'

    export default {

        components:{
            
        },

        data(){
            return{
                store
            }
        },
        
    }
</script>

<template>
    <header class="header">
        <div class="container">
            <div class="search-bar">
                <input class="header-input" type="text" v-model="userSearch" placeholder="Cerca il film o la serie tv">
                <button class="header-button"> Cerca </button>
            </div>

            <ul v-for="movie in movies" :key="movie.id">
                <li>
                    <h2>Film:</h2>
                    <h2>{{ movie.title }}</h2>
                    <h3>{{ movie.original_title }}</h3>
                    <p>{{ movie.original_language }}</p>
                    <p>{{ movie.vote_average }}</p>
                </li>
            </ul>
        </div>  
    </header>
</template>

<style lang="scss" scoped>
     .header-input{
        margin-top: 50px;
        padding: 10px;
    }

    .header-button{
        padding: 10px 15px;
        margin-left: 20px;
        background-color: black;
        color: white;
    }
</style>
