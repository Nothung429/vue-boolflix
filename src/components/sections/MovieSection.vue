<template>
    <div>
        <h2>Movies</h2>
        <ul class="row">
            <li class="movies col-2" v-for="(movie, index) in PageArray.movies" :key="index">
                <img :src="`https://image.tmdb.org/t/p/w154/${movie.poster_path}`" alt="">
                <h3>{{movie.title}}</h3>
                <h4>{{movie.original_title}}</h4>
                <h5>{{movie.vote_average}}</h5>
                <h6>{{movie.original_language}}</h6>
            </li>
        </ul>    
    </div>
</template>

<script>
    import PageArray from "../global/PageArray.js"

    export default {
        name: "MovieSection",
        data () {
            return {
                PageArray,
            }
        }
    }
</script>

<style lang="scss" scoped>
    .movies {
        color: blue;
    }    
</style>