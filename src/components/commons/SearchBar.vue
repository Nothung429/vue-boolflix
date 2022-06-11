<template>
    <div class="research">
        <form @submit.prevent = "searchBar()">
            <div class="research__input">
                <input type="text" placeholder="Search" v-model="selected">
            </div>
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
            display: flex;
            p {
                color: #fff;
            }
            input {
                padding: 5px 20px;
            }
        }
    }
</style>