<template>
  <div id="app">
    <MyHeader @searchText="getSearchText"/>
    <MyMain :listFilm="listFilm"/>
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
      listFilm: []
    }
  },
  components: {
    MyHeader,
    MyMain
  },
  methods: {
    getSearchText(text) {
      this.MySearchText = text;
      this.apiRequest();
    },
    apiRequest() {
                axios.get(`https://api.themoviedb.org/3/search/movie?api_key=c4a0217aed11ceee398209d64761d218&query=${this.MySearchText}&language=it-IT`)
                .then(response => {
                    this.listFilm = response.data.results;
                })
                .catch(err => {
                  console.log(err);
                })
            }
  }
}
</script>

<style lang="scss">

</style>
