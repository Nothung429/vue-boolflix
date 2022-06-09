<template>
    <header>
        <h1>Hello</h1>
        <div class="research">
            <form @submit.prevent = "searchBar()">
                <label>search movie</label>
                <input type="text" placeholder="Search" v-model="selectedMovie">
                <label>search tv-series</label>
                <input type="text" placeholder="Search" v-model="selectedTvSeries">
                <button type="submit">Search</button>
            </form>
        </div>
        <div class="movies__results">
            <ul>
                <li class="movies" v-for="(movie, index) in movies" :key="index">
                    <h3>{{movie.title}}</h3>
                    <h4>{{movie.original_title}}</h4>
                    <h5>{{movie.vote_average}}</h5>
                    <h6>{{movie.original_language}}</h6>
                </li>
            </ul>
            <ul>
                <li class="series" v-for="(tvSerie, index) in tvSeries" :key="index">
                    <h3>{{tvSerie.name}}</h3>
                    <h4>{{tvSerie.original_name}}</h4>
                    <h5>{{tvSerie.vote_average}}</h5>
                    <h6>{{tvSerie.original_language}}</h6>
                </li>
            </ul>
        </div>
    </header>
</template>

<script>
    import axios from "axios";

    export default {
        name: 'BaseHeader',
        data () {
            return {
                movies: [],
                tvSeries: [],
                selectedMovie: "",
                selectedTvSeries: "",

            }
        },
        methods: {
            searchBar() {
                axios.get("https://api.themoviedb.org/3/search/movie",
                {
                    params: {
                        api_key: "4adbf89faf8e1206e88d749b8cee0388",
                        query: this.selectedMovie,
                        language: "it-IT",
                    }
                }
                )
                .then((response) => {
                    this.movies = response.data.results;
                })
                .catch((error) => {
                    console.log(error);
                });

                axios.get("https://api.themoviedb.org/3/search/tv",
                {
                    params: {
                        api_key: "4adbf89faf8e1206e88d749b8cee0388",
                        query: this.selectedTvSeries,
                        language: "it-IT",
                    }
                }
                )
                .then((response) => {
                    this.tvSeries = response.data.results;
                })
                .catch((error) => {
                    console.log(error);
                });
            }
        },
    }
</script>

<style lang="scss" scoped>
    .series {
        color: blue;
    }
    .movies {
        color: red;
    }
</style>