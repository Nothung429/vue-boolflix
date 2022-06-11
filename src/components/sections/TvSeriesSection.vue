<template>
    <div>
        <h2 class="my-5">TV Series</h2>
        <ul class="row justify-content-center">
            <li class="series col-2 m-3 p-2" v-for="(tvSerie, index) in PageArray.tvSeries" :key="index">
                <img :src="`https://image.tmdb.org/t/p/w154/${tvSerie.poster_path}`" alt="">
                <h3>{{tvSerie.name}}</h3>
                <h4>{{tvSerie.original_name}}</h4>
                <h5>{{tvSerie.vote_average}}</h5>
                <img class="flag" :src="seriesFlag(tvSerie.original_language)" alt="language-flag">
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
            seriesFlag(language) {
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
        },
    }
</script>

<style lang="scss" scoped>
    .series {
        background-color: #0339fc;
        color: #fff;
        .flag {
            max-width: 100px;
        }
    }    
</style>