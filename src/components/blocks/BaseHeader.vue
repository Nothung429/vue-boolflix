<template>
    <header>
        <img src="https://media-assets.wired.it/photos/615ef4b55ccc3b73fb14d5b2/master/pass/wired_placeholder_dummy.png" alt="logo">
        <SearchBar/>
    </header>
</template>

<script>
    import SearchBar from '../commons/SearchBar.vue'

    export default {
        name: 'BaseHeader',
        components: {
            SearchBar,
        },        
    }
</script>

<style lang="scss" scoped>
    header {
        height: 100px;
        padding: 0 20px;
        background-color: #000;
        display: flex;
        justify-content: space-between;
        align-items: center;
        img {
            height: 100px;
        }
    }
</style>