<template>
    <div>
        <h2 class="my-5">TV Series</h2>
        <ul class="row justify-content-center">
            <li class="series col-2 m-3 p-2" v-for="(tvSerie, index) in PageArray.tvSeries" :key="index">
                <img :src="`https://image.tmdb.org/t/p/w154/${tvSerie.poster_path}`" alt="">
                <h3>{{tvSerie.name}}</h3>
                <h4>{{tvSerie.original_name}}</h4>
                <h5>{{tvSerie.vote_average}}</h5>
                <h6>{{tvSerie.original_language}}</h6>
            </li>
        </ul>
    </div>
</template>

<script>
    import PageArray from "../global/PageArray.js"

    export default {
        name: "TvSeriesSection",
        data () {
            return {
                PageArray,
            }
        }
    }
</script>

<style lang="scss" scoped>
    .series {
        background-color: #0339fc;
        color: #fff;
    }    
</style>