<script>

import store from '../data/store.js';


export default {
    components: {
    },

    data() {
        return {
            store,
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
    <div v-if="store.filmList != ''" class="founded-film">
        <h2>Film</h2>
    </div>
    <div class="contenitore">

        <div v-show="film.poster_path != null && film.backdrop_path != null" v-for="film, i in store.filmList"
            @mouseover="film.cardShow = true" @mouseleave="film.cardShow = false" class="card">

            <img v-if="film.cardShow == false"
                :src="store.prefissoImg + (film.poster_path == null ? film.backdrop_path : film.poster_path)" alt="">
            <div v-if="film.cardShow == true" class="details">
                <h2>{{ film.title }}</h2>
                <p v-if="film.original_title != film.title"><span class="red">Titolo originale:</span> {{
                    film.original_title }}</p>
                <div><span class="red">Lingua:</span><img :src="getFlegImg(film.original_language)" alt=""></div>
                <p>
                    <span><i :class="(film.vote_average >= 2) ? 'fa-solid fa-star' : 'fa-regular fa-star'"></i></span>
                    <span><i :class="(film.vote_average >= 4) ? 'fa-solid fa-star' : 'fa-regular fa-star'"></i></span>
                    <span><i :class="(film.vote_average >= 6) ? 'fa-solid fa-star' : 'fa-regular fa-star'"></i></span>
                    <span><i :class="(film.vote_average >= 8) ? 'fa-solid fa-star' : 'fa-regular fa-star'"></i></span>
                    <span><i :class="(film.vote_average == 10) ? 'fa-solid fa-star' : 'fa-regular fa-star'"></i></span>
                </p>
            </div>

        </div>

    </div>

</template>

<style scoped>
.founded-film {
    width: 80%;
    background-color: red;
    margin: 1rem auto;
    text-align: center;
}

.founded-film>h2 {
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