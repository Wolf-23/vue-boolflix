<template>
  <div id="app">
    <MyHeader @searchText="getSearchText"/>
    <MyMain :listFilm="listFilm" :listSerie="listSerie" :visibilityFilm="visibilityFilm" :visibilitySerie="visibilitySerie"/>
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
      visibilityFilm: false,
      visibilitySerie: false,
      apiUrl: 'https://api.themoviedb.org/3',
      apiKey: 'c4a0217aed11ceee398209d64761d218',
      apiLanguage: 'it-IT',
    }
  },
  components: {
    MyHeader,
    MyMain
  },
  methods: {
    getSearchText(text) {
      this.MySearchText = text.trim();
      const paramsObj = {
        params: {
          api_key: this.apiKey,
          language: this.language,
          query: text
        }
      }
      if (!this.MySearchText == '') {
        this.apiRequestFilm(paramsObj);
        this.apiRequestSerie(paramsObj);
        this.visibilityFilm = true;
        this.visibilitySerie = true;

      } else {
          this.listFilm = [];
          this.listSerie = [];
          this.visibilityFilm = false;
          this.visibilitySerie = false;
        }
    },
    apiRequestFilm(paramsObj) {
      axios.get(this.apiUrl + '/search/movie', paramsObj)
      .then(response => {
          this.listFilm = response.data.results;
      })
      .catch(err => {
        console.log(err);
      })
    },
    apiRequestSerie(paramsObj) {
        axios.get(this.apiUrl + '/search/tv', paramsObj)
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
