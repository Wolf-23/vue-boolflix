<template>
  <main>
      <h3 v-if="visibility == true">Lista Film Cercati:</h3>
      <ul v-for="(film, index) in listFilm" :key="index">
            <li class="title">{{film.title}}</li>
            <li>{{film.original_title}}</li>
            <li>{{film.original_language}}</li>
            <li>{{film.vote_average}}</li>
        </ul>
        <h3 v-if="visibility == true">Lista Serie Cercate:</h3>
        <ul v-for="(serie, index) in listSerie" :key="index">
            <li class="title">{{serie.name}}</li>
            <li>{{serie.original_name}}</li>
            <li>{{serie.original_language}}</li>
            <li>{{serie.vote_average}}</li>
        </ul>
  </main>
</template>

<script>
  
    export default {
        name: 'MyMain',
        props: {
            listFilm: Array,
            listSerie: Array,
            visibility: Boolean

        }
    }
</script>

<style scoped lang="scss">
    ul {
        border: 1px solid black;
        .title {
            font-size: 20px;
            font-weight: bold;
        }
    }
</style>