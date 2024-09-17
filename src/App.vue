<script>
import AppMain from './components/AppMain.vue';
import AppHeader from './components/AppHeader.vue';
import store from './data/store.js';
import axios from 'axios';



export default {
  components: {
    AppHeader,
    AppMain,
  },

  data() {
    return {
      store,
      cardShow: false,
    }
  },
  methods: {

  },
  created() {
    const optionsPopolar = {
      method: 'GET',
      url: 'https://api.themoviedb.org/3/trending/movie/day',
      params: { language: 'en-US', page: '1' },
      headers: {
        accept: 'application/json',
        Authorization: 'Bearer eyJhbGciOiJIUzI1NiJ9.eyJhdWQiOiJlZDJiNGYwZWY0YjgwZmEwOTBlNzU1OWM5ODNkMzk4ZSIsInN1YiI6IjY2NTczNzRmMDhkM2I5NmJlZTIxNWFkZCIsInNjb3BlcyI6WyJhcGlfcmVhZCJdLCJ2ZXJzaW9uIjoxfQ.2RYI6TSOgVLTYH0LBP9wtJR0Rqw_VPkiXHpH7mf9YsE'
      }
    };

    axios
      .request(optionsPopolar)
      .then((response) => {
        this.store.popolarFilmList = response.data.results
        for (let index = 0; index < this.store.popolarFilmList.length; index++) {
          this.store.popolarFilmList[index].cardShow = this.cardShow
        }
        console.log(this.store.popolarFilmList);
      })
      .catch(function (error) {
        console.error(error);
      });

    const optionsPopolarSerie = {
      method: 'GET',
      url: 'https://api.themoviedb.org/3/trending/tv/day',
      params: { language: 'en-US', page: '1' },
      headers: {
        accept: 'application/json',
        Authorization: 'Bearer eyJhbGciOiJIUzI1NiJ9.eyJhdWQiOiJlZDJiNGYwZWY0YjgwZmEwOTBlNzU1OWM5ODNkMzk4ZSIsInN1YiI6IjY2NTczNzRmMDhkM2I5NmJlZTIxNWFkZCIsInNjb3BlcyI6WyJhcGlfcmVhZCJdLCJ2ZXJzaW9uIjoxfQ.2RYI6TSOgVLTYH0LBP9wtJR0Rqw_VPkiXHpH7mf9YsE'
      }
    };

    axios
      .request(optionsPopolarSerie)
      .then((response) => {
        this.store.popolarSerieList = response.data.results
        for (let index = 0; index < this.store.popolarSerieList.length; index++) {
          this.store.popolarSerieList[index].cardShow = this.cardShow
        }
        console.log(this.store.popolarSerieList);
      })
      .catch(function (error) {
        console.error(error);
      });

  },
  mounted() {

  },
  computed: {

  },
}

</script>

<template>

  <AppHeader />

  <AppMain />


</template>

<style scoped></style>
