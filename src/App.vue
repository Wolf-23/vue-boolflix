<template>
  <div id="app">
    <MyHeader @searchText="getSearchText"/>
    <MyMain :listFilm="listFilm" :listSerie="listSerie"/>
  </div>
</template>

<script>
import MyHeader from './components/MyHeader.vue'
import MyMain from './components/MyMain.vue';
import axios from 'axios';
export default {
  name: 'App',
  data() {
    return {
      MySearchText: '',
      listFilm: [],
      listSerie: [],
    }
  },
  components: {
    MyHeader,
    MyMain
  },
  methods: {
    getSearchText(text) {
      this.MySearchText = text.trim();
      if (!this.MySearchText == '') {
        this.apiRequestFilm();
        this.apiRequestSerie();
      } else {
          this.listFilm = [];
          this.listSerie = [];
        }
    },
    apiRequestFilm() {
      axios.get(`https://api.themoviedb.org/3/search/movie?api_key=c4a0217aed11ceee398209d64761d218&language=it-IT&query=${this.MySearchText}`)
      .then(response => {
          this.listFilm = response.data.results;
      })
      .catch(err => {
        console.log(err);
      })
    },
    apiRequestSerie() {
        axios.get(`https://api.themoviedb.org/3/search/tv?api_key=c4a0217aed11ceee398209d64761d218&language=it-IT&query=${this.MySearchText}`)
        .then(response => {
            this.listSerie = response.data.results;
        })
        .catch(err => {
          console.log(err);
        })
    }
  }
}
</script>

<style lang="scss">
  @import './assets/styles/general.scss';
</style>
