<template>
    <main>
        <div class="container-custom">
            <MovieSection/>
            <TvSeriesSection/>
        </div>
    </main>
</template>

<script>
    import MovieSection from '../sections/MovieSection.vue'
    import TvSeriesSection from '../sections/TvSeriesSection.vue'

    export default {
        components: {
            MovieSection,
            TvSeriesSection,
        }
    }
</script>

<style lang="scss" scoped>

</style>