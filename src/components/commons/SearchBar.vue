<template>
    <div class="research">
        <form @submit.prevent = "searchBar()" class="d-flex">
            <input class="me-3" type="text" placeholder="Search" v-model="selected">
            <button type="submit">Search</button>
        </form>
    </div>
</template>

<script>
    import axios from "axios";
    import PageArray from "../global/PageArray.js"

    export default {
        name: 'SearchBar',
        data () {
            return {
                PageArray,
                selected: "",
            }
        },
        methods: {
            searchBar() {
                axios.get("https://api.themoviedb.org/3/search/movie",
                {
                    params: {
                        api_key: "4adbf89faf8e1206e88d749b8cee0388",
                        query: this.selected,
                        language: "it-IT",
                    }
                }
                )
                .then((response) => {
                    this.PageArray.movies = response.data.results;
                    this.selected = "";
                })
                .catch((error) => {
                    console.log(error);
                });

                axios.get("https://api.themoviedb.org/3/search/tv",
                {
                    params: {
                        api_key: "4adbf89faf8e1206e88d749b8cee0388",
                        query: this.selected,
                        language: "it-IT",
                    }
                }
                )
                .then((response) => {
                    this.PageArray.tvSeries = response.data.results;
                    this.selected = "";
                })
                .catch((error) => {
                    console.log(error);
                });
            }
        },
    }
</script>

<style lang="scss" scoped>
    .research {
        margin-right: 60px;
        form {
            input, button {
                background-color: #5b5b5b;
                color: #fff;
                border: none;
                padding: 5px 20px;
                border-radius: 10px;
            }
        }
    }
</style>