<template>
  <main>
    <div>
      <h3 v-if="visibility == true && this.listFilm.lenght > 0">Lista Film Cercati:</h3>
      <ul v-for="(film, index) in listFilm" :key="index">
            <li class="title">{{film.title}}</li>
            <li>{{film.original_title}}</li>
            <li>
                <img :src="getImage(film.original_language)" :alt="film.original_language">
            </li>
            <li>{{film.vote_average}}</li>
        </ul>
    </div>
    <div>
        <h3 v-if="visibility == true && this.listFilm.lenght > 0">Lista Serie Cercate:</h3>
        <ul v-for="(serie, index) in listSerie" :key="index">
            <li class="title">{{serie.name}}</li>
            <li>{{serie.original_name}}</li>
            <li><img :src="getImage(serie.original_language)" :alt="serie.original_language"></li>
            <li>{{serie.vote_average}}</li>
        </ul>
    </div>
  </main>
</template>

<script>
  
    export default {
        name: 'MyMain',
        props: {
            listFilm: Array,
            listSerie: Array,
            visibility: Boolean

        },
        data() {
            return {
            }
        },
        methods: {
            getImage(language) {
                let imageSrc = '';
                if(language == 'en' || language == 'it' || language == 'fr') {
                    imageSrc = require('../assets/flag/flag-of-' + language + '.png');
                } else {
                    imageSrc = language;
                }
                return imageSrc;
            }
        },
    }
</script>

<style scoped lang="scss">
    ul {
        border: 1px solid black;
        .title {
            font-size: 20px;
            font-weight: bold;
        }
        img {
            height: 20px;
        }
    }
</style>