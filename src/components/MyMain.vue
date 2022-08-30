<template>
  <main>
        <ul v-for="(film, index) in listFilm" :key="index">
            <li class="title">{{film.title}}</li>
            <li>{{film.original_title}}</li>
            <li>{{film.original_language}}</li>
            <li>{{film.vote_average}}</li>
        </ul>
  </main>
</template>

<script>
  
    export default {
        name: 'MyMain',
        props: {
            listFilm: Array
        },
        data() {
            return{
               
            }
        },
        methods: {
            
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
    }
</style>