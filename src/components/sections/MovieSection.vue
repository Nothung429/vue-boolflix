<template>
    <div>
        <h2 class="title-movie my-3">Movies</h2>
        <ul class="row justify-content-center">
            <li class="movies col-3 m-3" v-for="(movie, index) in PageArray.movies" :key="index" @mouseover="hover = true"
            @mouseleave="hover = false">
                <div class="movies__overlay p-2 overflow-auto" v-if="hover">
                    <h3>Titolo: <span>{{movie.title}}</span></h3>
                    <h4>Titolo Originale: <span>{{movie.original_title}}</span></h4>
                    <p class="stars" v-html="getVote(movie.vote_average)">Voto: </p>
                    <p>Lingua: <img class="flag" :src="movieFlag(movie.original_language)" alt="language-flag"></p>
                    <p>Sinossi: <span>{{movie.overview}}</span></p>
                </div>
                <img :src="getPoster(movie.poster_path)" :alt="movie.title">
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
                hover: false,
                DataFlags: {
                    it: "https://upload.wikimedia.org/wikipedia/commons/thumb/0/03/Flag_of_Italy.svg/280px-Flag_of_Italy.svg.png",
                    en: "https://www.mlaworld.com/wp-content/uploads/2021/07/metà-bandiera-americana-e-inglese.png",
                    es: "https://upload.wikimedia.org/wikipedia/commons/thumb/9/9a/Flag_of_Spain.svg/280px-Flag_of_Spain.svg.png",
                    fr: "https://upload.wikimedia.org/wikipedia/commons/thumb/b/bc/Flag_of_France_%281794–1815%2C_1830–1974%2C_2020–present%29.svg/280px-Flag_of_France_%281794–1815%2C_1830–1974%2C_2020–present%29.svg.png",
                    de: "https://upload.wikimedia.org/wikipedia/commons/thumb/b/ba/Flag_of_Germany.svg/280px-Flag_of_Germany.svg.png",
                    ja: "https://upload.wikimedia.org/wikipedia/commons/thumb/9/9e/Flag_of_Japan.svg/280px-Flag_of_Japan.svg.png",
                    ko: "https://upload.wikimedia.org/wikipedia/commons/thumb/0/09/Flag_of_South_Korea.svg/280px-Flag_of_South_Korea.svg.png",
                    tr: "https://upload.wikimedia.org/wikipedia/commons/thumb/b/b4/Flag_of_Turkey.svg/280px-Flag_of_Turkey.svg.png",
                    world: "https://upload.wikimedia.org/wikipedia/commons/thumb/2/2f/Flag_of_the_United_Nations.svg/220px-Flag_of_the_United_Nations.svg.png",
                },
            }
        },
        methods: {
            getPoster(poster) {
                if (poster === null) {
                    return `https://via.placeholder.com/300x400`
                } else {
                    return `https://image.tmdb.org/t/p/w342/${poster}`
                }
            },
            movieFlag(language) {
                if (language === "it") {
                    return this.DataFlags.it
                } else if (language === "en") {
                    return this.DataFlags.en
                } else if (language === "es") {
                    return this.DataFlags.es
                } else if (language === "fr") {
                    return this.DataFlags.fr
                } else if (language === "de") {
                    return this.DataFlags.de
                } else if (language === "ja") {
                    return this.DataFlags.ja
                } else if (language === "ko") {
                    return this.DataFlags.ko
                } else if (language === "tr") {
                    return this.DataFlags.tr
                } else {
                    return this.DataFlags.world
                }
            },
            getVote(vote) {
                let fullStar = "";
                let emptyStar = "";
                for (let i = 0 ; i < (Math.ceil(vote / 2)) ; i++) {
                    fullStar += `<i class="fa-solid fa-star"></i> `;
                }
                for (let i = 0 ; i < (5 - Math.ceil(vote / 2)) ; i++) {
                    emptyStar += `<i class="fa-regular fa-star"></i> `;
                }
                return `${fullStar}${emptyStar}`;                
            }
        },
    }
</script>

<style lang="scss" scoped>
    .title-movie {
        color: #fff;
        font-size: 46px;
    }
    .movies {
        position: relative;
        color: #fff;
        height: 400px;
        width: 300px;
        .stars {
            color: #eba834;
        }
        .flag {
            max-width: 60px;
        }
        img {
            width: 100%;
            height: 100%;
        }
        &__overlay {
            position: absolute;
            top: 0;
            left: 0;
            right: 0;
            bottom: 0;
            z-index: 1;
            background-color: rgba(0,0,0,0.9);
            opacity: 1;
            span {
                color: #878683;
            }
        }
    }
</style>