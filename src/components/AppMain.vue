<script>
import FilmLine from './FilmLine.vue';
import SeriesTvLine from './SeriesTvLine.vue';
import PopolarTranding from './PopolarTranding.vue';
import PopolarSeriesTv from './PopolarSeriesTv.vue';
import store from '../data/store.js';
import axios from 'axios';



export default {
    components: {
        FilmLine,
        SeriesTvLine,
        PopolarTranding,
        PopolarSeriesTv,
    },

    data() {
        return {
            store,

        }
    },
    methods: {

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

    <PopolarTranding v-if="store.popolar == false" />

    <PopolarSeriesTv v-if="store.popolar == false" />

    <FilmLine v-if="store.popolar == true" />

    <SeriesTvLine v-if="store.popolar == true" />

</template>

<style scoped></style>