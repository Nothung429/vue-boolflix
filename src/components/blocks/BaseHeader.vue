<template>
    <header>
        <h1>Hello</h1>
        <div class="research">
            <form action="">
                <input type="text" placeholder="Search">
                <button>Search</button>
            </form>
        </div>
        <div class="movies__results">
            <ul>
                <li v-for="(movie, index) in movies" :key="index">{{movie.title}}</li>
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
            }
        },
        created() {
            axios.get("https://api.themoviedb.org/3/search/movie",
                {
                    params: {
                        api_key: '4adbf89faf8e1206e88d749b8cee0388',
                        query: 'godzilla',
                        language: 'it-IT',
                    }
                }
            )
            .then((response) => {
                this.movies = response.data.results;
            })
            .catch((error) => {
                console.log(error);
            });
        },
    }
</script>

<style lang="scss" scoped>

</style>