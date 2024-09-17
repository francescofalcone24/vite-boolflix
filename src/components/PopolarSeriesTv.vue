<script>

import store from '../data/store.js';


export default {
    components: {
    },

    data() {
        return {
            store,
            svg: '.svg',
            imgAsset: '../assets/img/'
        }
    },
    methods: {
        getFlegImg(path) {
            let risultato = new URL(`../assets/img/${path}.svg`, import.meta.url);
            return risultato.href;
        }
    },
    created() {

    },
    mounted() {

    },
    computed: {

    },
}

</script>

<template>
    <div class="founded-serie">
        <h2>Most Popolar Series</h2>
    </div>
    <div class="contenitore">

        <div v-show="serie.poster_path != null && serie.backdrop_path != null"
            v-for="serie, i in store.popolarSerieList" @mouseover="serie.cardShow = true"
            @mouseleave="serie.cardShow = false" class="card">

            <img v-if="serie.cardShow == false"
                :src="store.prefissoImg + (serie.poster_path == null ? serie.backdrop_path : serie.poster_path)" alt="">
            <div v-if="serie.cardShow == true" class="details">
                <h2>{{ serie.name }}</h2>
                <p v-if="serie.original_name != serie.name"><span class="red">Titolo originale:</span> {{
                    serie.original_name }}</p>
                <div><span class="red">Lingua:</span><img :src="getFlegImg(serie.original_language)" alt=""></div>
                <p>
                    <span><i :class="(serie.vote_average >= 2) ? 'fa-solid fa-star' : 'fa-regular fa-star'"></i></span>
                    <span><i :class="(serie.vote_average >= 4) ? 'fa-solid fa-star' : 'fa-regular fa-star'"></i></span>
                    <span><i :class="(serie.vote_average >= 6) ? 'fa-solid fa-star' : 'fa-regular fa-star'"></i></span>
                    <span><i :class="(serie.vote_average >= 8) ? 'fa-solid fa-star' : 'fa-regular fa-star'"></i></span>
                    <span><i :class="(serie.vote_average == 10) ? 'fa-solid fa-star' : 'fa-regular fa-star'"></i></span>
                </p>
            </div>

        </div>

    </div>

</template>

<style scoped>
.founded-serie {
    width: 80%;
    background-color: red;
    margin: 1rem auto;
    text-align: center;
}

.founded-serie>h2 {
    color: white;
    padding: 0.5rem;
}


.contenitore {
    width: 80%;
    margin: 2rem auto;
    display: flex;
    flex-wrap: wrap;
}

.card {
    text-align: center;
    width: calc(100% / 6);
    min-height: 20rem;
    padding: 1rem;
}

.card>img {
    width: 90%;
}

.details>div>img {
    width: 7%;
    padding-top: 0.1rem;
}

.details>div {
    padding-bottom: 0.5rem;
}

p {
    margin-bottom: 0.5rem;
    color: white;
}

.details>h2 {
    margin-bottom: 1rem;
    color: white;
}


.red {
    color: red;
    margin-right: 0.1rem;
}

.fa-solid {
    color: gold;
}
</style>